# vim-rails commands





## Install the vim-ruby and vim-rails plugins

1. **Create the Plugin Directory (if it doesn’t already exist):**

Vim typically looks for plugins in the `~/.vim/pack/plugins/start/` directory. 

```bash
mkdir -p ~/.vim/pack/plugins/start
```

2. **Clone the plugins directly into this directory so that Vim loads them automatically.**

```bash
git clone https://github.com/vim-ruby/vim-ruby.git ~/.vim/pack/plugins/start/vim-ruby
git clone https://github.com/tpope/vim-rails.git ~/.vim/pack/plugins/start/vim-rails
```

3. **Check if the vim-ruby and vim-rails plugins are Loaded in Vim:**

```bash
:scriptnames
```

To check for the following lines:

```bash
~/.vim/pack/plugins/start/vim-ruby/ftplugin/ruby.vim
~/.vim/pack/plugins/start/vim-ruby/indent/ruby.vim
~/.vim/pack/plugins/start/vim-ruby/syntax/ruby.vim
~/.vim/pack/plugins/start/vim-rails/plugin/rails.vim
```

4. **Manually Adding to runtimepath (Optional), if the plugins don’t load automatically.**

```bash
set runtimepath+=~/.vim/pack/plugins/start/vim-ruby
set runtimepath+=~/.vim/pack/plugins/start/vim-rails
```



## Switch between related files

:V equals to :RV, and opens the related files in a vertical splitted window. :S works horizotally.

==Use :V and tab to find out what commands are available.==

```bash
:Vmodel			// Opens the corresponding model file.
:Vmigration

:VController		// Opens the corresponding controller file.

:Vview edit		// In a controller or view file, this open the edit view.
:Vview new		// In a controller or view file, this open the new view.

:Vlayout
:Vstylesheet
```

## Switch between the production code and a test.

:AV opens the related test files vertically, and with :AS horizontally. 

## :Extract partial

When working with views, you can simply move code into partials by highlighting the code and executing the command `:Extract ‘patial_name’`. This will generate the file with `_`, move the code into it, and also replace the code to `render :partial_name` in the original file.











https://medium.com/@grzegorz.smajdor/ruby-on-rails-and-vim-6bcf84e0bc08





------



# *rails.txt*

Plugin for working with Ruby on Rails applications

Author:  Tim Pope <http://tpo.pe/>

|rails-introduction|            Introduction and Feature Summary
|rails-navigation|              Navigation
|rails-gf|                          File Under Cursor - gf
|rails-alternate-related|           Alternate and Related Files
|rails-type-navigation|             File Type Commands
|rails-exec|                    Executable Wrappers
|rails-refactoring|             Refactoring Helpers
|rails-partials|                    Partial Extraction
|rails-migrations|                  Migration Inversion
|rails-misc|                    Miscellaneous Commands
|rails-integration|             Integration
|rails-vim-integration|             Integration with the Vim Universe
|rails-rails-integration|           Integration with the Rails Universe
|rails-syntax|                  Syntax Highlighting
|rails-projections|             Projections
|rails-configuration|           Configuration
|rails-global-settings|         Global Settings
|rails-about|                   About rails.vim
|rails-license|                     License

INTRODUCTION					*rails-introduction* *rails*

Whenever you edit a file in a Rails application, this plugin will be
automatically activated.  This sets various options and defines a few
buffer-specific commands.

If you are in a hurry to get started, with a minimal amount of reading, you
are encouraged to at least skim through the headings and command names in this
file, to get a better idea of what is offered.  If you only read one thing,
make sure it is the navigation section.

NAVIGATION					*rails-navigation*

Navigating the twisted file hierarchy of Rails projects is what initially
inspired the creation of this plugin.

The standard Rails load path is prepended to 'path', enabling |:find| to work:
>
	:find application_controller
<
In asset files, 'path' is instead set to the asset load path, and
'suffixesadd' is set to a long list of possible JavaScript or CSS suffixes.

File Under Cursor - gf ~
						*rails-gf*
The |gf| command, which normally edits the current file under the cursor, has
been remapped to take context into account.  |CTRL-W_f| (open in new window),
|CTRL-W_gf| (open in new tab), and |c_CTRL-R_CTRL-F| (insert filename on
command line) are also remapped.

Example uses of |gf|, and where they might lead.
(* indicates cursor position)
>
	Pos*t.first
<	app/models/post.rb ~
>
	has_many :c*omments
<	app/models/comment.rb ~
>
	link_to 'Home', :controller => 'bl*og'
<	app/controllers/blog_controller.rb ~
>
	<%= render 'sh*ared/sidebar' %>
<	app/views/shared/_sidebar.html.erb ~
>
	<%= stylesheet_link_tag 'appl*ication' %>
<	app/assets/stylesheets/application.css ~
>
	class BlogController < Applica*tionController
<	app/controllers/application_controller.rb ~
>
	class ApplicationController < ActionCont*roller::Base
<	.../action_controller/base.rb ~
>
	fixtures :pos*ts
<	test/fixtures/posts.yml ~
>
	layout :pri*nt
<	app/views/layouts/print.html.erb ~
>
	<%= link_to "New", new_comme*nt_path %>
<	app/controllers/comments_controller.rb (jumps to def new) ~

In the last example, the controller and action for the named route are
determined by evaluating routes.rb as Ruby and doing some introspection.  This
means code from the application is executed.  Keep this in mind when
navigating unfamiliar applications.

Alternate and Related Files ~
						*rails-alternate-related*
Two commands, :A and :R, are used to quickly jump to an "alternate" and a
"related" file, defined below.

	*rails-:A* *rails-:AE* *rails-:AS* *rails-:AV* *rails-:AT* *rails-:AD*
:A			These commands were picked to mimic Michael Sharpe's
:AE			a.vim.  Briefly, they edit the "alternate" file, in
:AS			either the same window (:A and :AE), a new split
:AV			window (:AS), a new vertically split window (:AV), a
:AT			new tab (:AT), or read it into the current buffer
:AD			(:AD).  With a range (:.A), they find the "related"
			file for the specified line.  With a filename
			argument, they edit a file relative to the application
			root (:A Rakefile), and with both a count and a
			filename (:1A post.rb), they find a file in 'path',
			similar to |:find| but with smarter tab completion.

	*rails-:R* *rails-:RE* *rails-:RS* *rails-:RV* *rails-:RT* *rails-:RD*
:R			These are similar |rails-:A| and friends above, only
:RE			they default to the "related" file rather than the
:RS			"alternate."  :R is equivalent to :.A and :0R is
:RV			equivalent to :.A.  The filename and count version
:RT			(:1R post.rb) is hard coded to use the application
:RD			load path rather than 'path', so that one can access
			Ruby files regardless of 'filetype'.

					*rails-alternate* *rails-related*
The alternate file is most frequently the test file, though there are
exceptions.  The related file varies, and is sometimes dependent on current
location in the file.  For example, when editing a controller, the related
file is template for the method currently being edited.

The easiest way to learn these commands is to experiment.  A few examples of
alternate and related files for a Test::Unit application follow:

Current file		Alternate file		Related file ~
model			unit test		schema definition
controller (in method)	functional test		template (view)
template (view)		functional test  	controller (jump to method)
migration		previous migration	next migration
database.yml		database.example.yml	environments/*.rb

Alternates can be tweaked with |rails-projections|.

File Type Navigation Commands ~
						*rails-type-navigation*
For the less common cases, a more deliberate set of commands are provided.
Each of the upcoming commands takes an optional argument (with tab completion)
but defaults to a reasonable guess.  Commands that default to the current
model or controller generally behave like you'd expect in other file types.
For example, in app/helpers/posts_helper.rb, the current controller is
"posts", and in test/fixtures/comments.yml, the current model is "comment".
In model related files, the current controller is the pluralized model name,
and in controller related files, the current model is the singularized
controller name.

Each of the following commands has variants for splitting, vertical splitting,
opening in a new tab, and reading the file into the current buffer.  For
:Emodel, those variants would be :Smodel, :Vmodel, :Tmodel, and :Dmodel.
They also allow for jumping to methods or line numbers using the same syntax
as |:rails-R|, and file creation (with a bit of boilerplate) can be forced by
adding a ! after the filename (not after the command itself!).

Additionally, for each unrecognized directory of the form app/{type}s/
containing at least one file matching *_{type}.rb, a command of the form
:E{type} is automatically defined.

:Econtroller					|rails-:Econtroller|
:Eenvironment					|rails-:Eenvironment|
:Efixtures					|rails-:Efixtures|
:Efunctionaltest				|rails-:Efunctionaltest|
:Ehelper					|rails-:Ehelper|
:Einitializer					|rails-:Einitializer|
:Eintegrationtest				|rails-:Eintegrationtest|
:Ejavascript					|rails-:Ejavascript|
:Elayout					|rails-:Elayout|
:Elib						|rails-:Elib|
:Elocale					|rails-:Elocale|
:Emailer					|rails-:Emailer|
:Emigration					|rails-:Emigration|
:Emodel						|rails-:Emodel|
:Eschema					|rails-:Eschema|
:Espec						|rails-:Espec|
:Estylesheet					|rails-:Estylesheet|
:Etask						|rails-:Etask|
:Eunittest					|rails-:Eunittest|
:Eview						|rails-:Eview|

				*rails-:Econtroller* *rails-:Rcontroller*
:Econtroller [{name}]	Edit the specified or current controller.

				*rails-:Eenvironment* *rails-:Renvironment*
:Eenvironment [{name}]  Edit the config/environments file specified.  With no
			argument, defaults to editing config/application.rb
			or config/environment.rb.

				*rails-:Efixtures* *rails-:Rfixtures*
:Efixtures [{name}]	Edit the fixtures for the given or current model.  If
			an argument is given, it must be pluralized, like the
			final filename (this may change in the future).  If
			omitted, the current model is pluralized.  An optional
			extension can be given, to distinguish between YAML
			and CSV fixtures.

			*rails-:Efunctionaltest* *rails-:Rfunctionaltest*
:Efunctionaltest [{name}]
			Edit the functional test or controller spec for the
			specified or current controller.

				*rails-:Ehelper* *rails-:Rhelper*
:Ehelper [{name}]	Edit the helper for the specified name or current
			controller.

				*rails-:Einitializer* *rails-:Rinitializer*
:Einitializer [{name}]  Edit the config/initializers file specified.  With no
			argument, defaults to editing config/routes.rb.

			*rails-:Eintegrationtest* *rails-:Rintegrationtest*
:Eintegrationtest [{name}]
			Edit the integration test, integration spec, or
			cucumber feature specified.  With no argument,
			defaults to editing test/test_helper.rb.

				*rails-:Ejavascript* *rails-:Rjavascript*
:Ejavascript [{name}]	Edit the JavaScript for the specified name or current
			controller.  Also supports CoffeeScript in
			app/scripts/.

				*rails-:Elayout* *rails-:Rlayout*
:Elayout [{name}]	Edit the specified layout.  Defaults to the layout for
			the current controller, or the application layout if
			that cannot be found.  A new layout will be created if
			an extension is given.

				*rails-:Elib* *rails-:Rlib*
:Elib [{name}]		Edit the library from the lib directory for the
			specified name.  With no argument, defaults to editing
			the application Gemfile (a task formally handled by
			the defunct :Rplugin).

				*rails-:Elocale* *rails-:Rlocale*
:Elocale [{name}]	Edit the config/locale file specified, optionally
			adding a yml or rb extension if none is given.  With
			no argument, checks config/environment.rb for the
			default locale.

				*rails-:Emailer* *rails-:Rmailer*
:Emailer [{name}]	Edit the specified mailer.

				*rails-:Emigration* *rails-:Rmigration*
:Emigration [{pattern}]	If {pattern} is a number, find the migration for that
			particular set of digits, zero-padding if necessary.
			Otherwise, find the newest migration containing the
			given pattern.  Omitting the pattern selects the
			latest migration.  Give a numeric argument of 0 to edit
			db/seeds.rb.

				*rails-:Emodel* *rails-:Rmodel*
:Emodel [{name}]	Edit the specified or current model.

				*rails-:Espec* *rails-:Rspec*
:Espec [{name}]		Edit the given spec.  With no argument, defaults to
			editing spec/spec_helper.rb (If you want to jump to
			the spec for the given file, use |rails-:A| instead).
			This command is only defined if there is a spec folder
			in the root of the application.

				*rails-:Eschema* *rails-:Rschema*
:Eschema [{table}]	Edit the schema and optionally jump to the specified
			table.

				*rails-:Estylesheet* *rails-:Rstylesheet*
:Estylesheet [{name}]	Edit the stylesheet for the specified name or current
			controller.  Also supports Sass and SCSS.

				*rails-:Etask* *rails-:Rtask*
:Etask [{name}]		Edit the .rake file from lib/tasks for the specified
			name.  If no argument is given, the application
			Rakefile is edited.

				*rails-:Eunittest* *rails-:Runittest*
:Eunittest [{name}]	Edit the unit test or model spec for the specified
			name or current model.

				*rails-:Eview* *rails-:Rview*
:Eview [[{controller}/]{view}]
			Edit the specified view.  The controller will default
			sensibly, and the view name can be omitted when
			editing a method of a controller.  If a view name is
			given with an extension, a new file will be created.
			This is a quick way to create a new view.

Finally, one Vim feature that proves helpful in conjunction with all of the
above is |CTRL-^|.  This keystroke edits the previous file, and is helpful to
back out of any of the above commands.

EXECUTABLE WRAPPERS				*rails-exec*

Several commands are provided that wrap the `rails` and `rake` executables.
Additionally, `rails` (or `rake` on Rails versions older than 5) can be
invoked directly with |:make| or dispatch.vim's :Make.

						*rails-:Rails*
:Rails {command} [options]
			Invoke "rails {command}".  On older versions of Rails,
			it will conditionally invoke "rake {command}" and
			"script/{command}" when appropriate.  Uses |:!| or
			dispatch.vim's :Start if the command is "console",
			"dbconsole", or "server".  Otherwise, the "rails"
			|:compiler| plugin included with the plugin is
			temporarily enabled, and |:make|  or dispatch.vim's
			:Make is used to load the output into the quickfix
			list.
			Unlike other commands, :Rails is available globally,
			for use with the "new" subcommand.

:Rails			With no command, runs a default task based on the
			current file.  See |rails-default-task|.

						*rails-:Rscript*
:Rscript {command} [options]
			Deprecated alias for |:Rails| {command}.

						*rails-:Console*
:Console {options}	Launch rails console {options}. If dispatch.vim's
			:Start is available, that is used.  Otherwise,
			executes directly in the foreground.

					*rails-:Generate* *rails-:Rgenerate*
:Generate {options}	Invoke rails generate {options} and loads the
			generated files into the quickfix list.  Use ! to
			suppress jumping to the first file.

					*rails-:Destroy* *rails-:Rdestroy*
:Destroy {options}	Invoke rails destroy {options} and loads the destroyed
			files into the quickfix list.

					*rails-:Server* *rails-:Rserver*
:Server {options}	Launch rails server {options} in the background.  If
			dispatch.vim's :Start is available, that is used.
			Otherwise, the --daemon option is passed in.

					*rails-:Server!* *rails-:Rserver!*
:Server! {options}	Kill the pid found in tmp/pids/server.pid and then
			invoke :Server.

					*rails-:Runner* *rails-:Rrunner*
:[range]Runner [file]	Run the given file or code with rails runner and load
:Runner {code}		the results in to the quickfix list, using the error
			parser from the "ruby" |:compiler|.  If the file looks
			like a test, spec, or cucumber feature, the
			"rubyunit", "rspec", or "cucumber" |:compiler| will be
			used instead.  If provided, [range] is passed to the
			test runner to restrict execution to a particular
			line.  With no argument, defaults to running the test
			for the current file.

						*rails-:Rp*
:[range]Rp {code}	Use rails runner to execute "p begin {code} end" and
			echo the result.

						*rails-:Rpp*
:[range]Rpp {code}	Like :Rp, but with pp (pretty print).

						*rails-:Rake*
:[range]Rake {task}	Invoke `rake`.  Generally, you are encouraged to use
			|:Rails| or directly invoke |:make| instead.

						*rails-default-task*

Invoking |:Rails| with no arguments runs a default task.  This is typically
the associated test task, but can also be a closely related utility task.

File                            Task ~
test/*_test.rb                  test TEST=test/*_test.rb
spec/*_spec.rb                  spec SPEC=spec/*_spec.rb
features/*.feature              cucumber FEATURE=features/*.feature
app/*.rb                        test TEST=... | spec SPEC=...
test/fixtures/*.yml             db:fixtures:load FIXTURES=*
config.ru                       middleware
config/routes.rb                routes
db/migrate/*_*.rb               db:migrate:redo VERSION=*
db/schema.rb                    db:migrate:status
db/seeds.rb                     db:seed
README                          about

For some files, giving the command a range (e.g., :.Rails) triggers a variant
of the task to be performed.

File                            Task when given range ~
test/*_test.rb                  test TEST=test/*_test.rb TESTOPTS=-n<method>
spec/*_spec.rb                  spec SPEC=spec/*_spec.rb:<line>
features/*.feature              cucumber FEATURE=features/*.feature:<line>
test/fixtures/*.yml             db:fixtures:identify LABEL=<label>
db/migrate/*_*.rb               db:migrate:down VERSION=*
lib/tasks/*.rake                <try to guess currently edited task>

You can override the default task with a comment like "# rails <task>" either
at the top of the file or before the method referenced by the given line
number.

If dispatch.vim is installed, you can also run the default task by calling
|:Dispatch| with no arguments.  Use :.FocusDispatch and :0FocusDispatch to see
the default task with and without a range given.

REFACTORING HELPERS				*rails-refactoring*

A few features are dedicated to helping you refactor your code.

Partial Extraction ~
						*rails-partials*

The :Extract command can be used to extract part of a view to a partial, part
of a helper to another helper, or part of a model or controller to a concern.

					*rails-:Extract* *rails-:Rextract*
:[range]Extract [{controller}/]{name}
			Create a {name} partial from [range] lines (default:
			current line).  Only available in views.

:[range]Extract {helper}
			Create a {name} helper from [range] lines (default:
			current line).  Only available in helpers.

:[range]Extract {concern}
			Create a {name} concern from [range] lines (default:
			current line).  Only available in models and
			controllers.

If this is your file, in app/views/blog/show.html.erb: >

 1	<div>
 2	  <h2><%= @post.title %></h2>
 3	  <p><%= @post.body %></p>
 4	</div>

And you issue this command: >

	:2,3Extract post

Your file will change to this: >

 1	<div>
 2	  <%= render "post" %>
 3	</div>

And app/views/blog/_post.html.erb will now contain: >

 1	<h2><%= @post.title %></h2>
 2	<p><%= @post.body %></p>
<
The easiest way to choose what to extract is to use |linewise-visual| mode.
Then, a simple >
	:'<,'>Extract blog/post
will suffice. (Note the use of a controller name in this example.)

Migration Inversion ~
					*rails-migrations* *rails-:Rinvert*
:Rinvert		In a migration, rewrite the self.up method into a
			self.down method.  If self.up is empty, the process is
			reversed.  This chokes on more complicated
			instructions, but works reasonably well for simple
			calls to create_table, add_column, and the like.
			Newer versions of Rails provide increasingly good
			support for reversible migration definitions, so this
			command is deprecated and no longer maintained.

MISCELLANEOUS COMMANDS				*rails-misc*

						*rails-:Clog*
:Clog [environment]	Load the log file for the given environment using
			|:cgetfile|, open the quickfix window, and jump to the
			last line.  |R| is remapped to reload the list, and
			|G| remapped to do the same before it's usual behavior
			of jumping to the last line.  If the delay in loading
			is too long, you might consider :Rails log:clear.

						*rails-:Rlog*
:Rlog [environment]	Open the log file in the preview window using
			|:pedit|.  Deprecated in favor if |rails-:Clog|.

					*rails-:Preview* *rails-:Rpreview*
:Preview [path]		Open the given path for the current app in a browser.
			The host and port are determined by applying some
			netstat/lsof trickery to the current server pid.  If
			no server is running, Pow is consulted, and if all
			else fails, a default of localhost:3000 is used.  If
			no path is given, a default is used based on the
			current file and the application's routes.  The
			default is overridden by comments like the following
			that are either before the current method call or at
			the top of the file: >

		# GET /users
		# PUT /users/1
<
			If it's not using the right browser, define an OpenURL
			command:
>
		:command -bar -nargs=1 OpenURL :!open <args>
<
					*rails-:Preview!* *rails-:Rpreview!*
:Preview! [path]	Like :Preview, but open the path inside Vim using
			|netrw| instead.

						*rails-:Rrefresh*
:Rrefresh		Refreshes cached settings.

						*rails-:Rrefresh!*
:Rrefresh!		As above, and also reloads rails.vim.

						*rails-:Cd* *rails-:Rcd*
						*rails-:Lcd* *rails-:Rlcd*
:Cd [{directory}]	These have been removed.  Install projectionist.vim
:Lcd [{directory}]	for a replacement.

						*rails-:Ctags* *rails-:Rtags*
:Ctags			Calls ctags -R on the current application root.
			Exuberant ctags must be installed.  Additional
			arguments can be passed to ctags with
			|g:rails_ctags_arguments|.

INTEGRATION					*rails-integration*

Having one foot in Rails and one in Vim, rails.vim has two worlds with which
to interact.

Integration with the Vim Universe ~
						*rails-vim-integration*

A handful of Vim plugins are enhanced by rails.vim.  All plugins mentioned can
be found at http://www.vim.org/.

						*rails-dadbod*
Created by yours truly, dadbod.vim is a modern take on a Vim database plugin.
This plugin sets the dadbod.vim default to the application's development
database, and also provides an interface for accessing any environment of any
Rails app:
>
  :DB rails:#production
  :DB rails:/path/to/app
  :DB rails:/path/to/app#production
<
						*rails-:Rdbext* *rails-dbext*
Native support for dbext has been removed.  Install dadbod.vim and enable
|g:dadbod_manage_dbext| to achieve the same effect.

						*rails-surround*
The |surround| plugin available from vim.org enables adding and removing
"surroundings" like parentheses, quotes, and HTML tags.  Even by itself, it is
quite useful for Rails development, particularly eRuby editing.  When coupled
with this plugin, a few additional replacement surroundings are available in
eRuby files.  See the |surround| documentation for details on how to use them.
The table below uses ^ to represent the position of the surrounded text.

Key	Surrounding ~
=	<%= ^ %>
-	<% ^ -%>
#	<%# ^ %>
<C-E>	<% ^ -%>\n<% end -%>

The last surrounding is particularly useful in insert mode with the following
map in one's vimrc.  Use Alt+o to open a new line below the current one.  This
works nicely even in a terminal (where most alt/meta maps will fail) because
most terminals send <M-o> as <Esc>o anyways.
>
	imap <M-o> <Esc>o
<
One can also use the <C-E> surrounding in a plain Ruby file to append a bare
"end" on the following line.

						*rails-abolish*
Among the many features of |abolish| on vim.org is the ability to change the
inflection of the word under the cursor.  For example, one can hit crs to
change from MixedCase to snake_case.  This plugin adds two additional
inflections: crl for alternating between the singular and plural, and crt for
altering between tableize and classify.  The latter is useful in changing
constructs like BlogPost.all to current_user.blog_posts.all and vice versa.

						*rails-rspec*
The presence of a spec directory causes several additional behaviors to
activate.  :A knows about specs and will jump to them (but Test::Unit files
still get priority).  The associated controller or model of a spec is
detected, so all navigation commands should work as expected inside a spec
file.  :Rails in a spec runs just that spec, and in a model, controller, or
helper, runs the associated spec.

:Eunittest and :Efunctionaltest lead double lives, handling model/helper and
controller/mailer specs respectively.  For everything else, you can use
:Espec.

ABBREVIATIONS				*rails-abbreviations* *rails-snippets*

Abbreviations have been removed without replacement.

SYNTAX HIGHLIGHTING				*rails-syntax*

Syntax highlighting is by and large a transparent process.  For the full
effect, however, you need a colorscheme which accentuates rails.vim
extensions.  One such colorscheme is vividchalk, available from vim.org.

The following is a summary of the changes made by rails.vim to the standard
syntax highlighting.

						*rails-syntax-keywords*
Rails specific keywords are highlighted in a filetype specific manner.  For
example, in a model, has_many is highlighted, whereas in a controller,
before_filter is highlighted.  A wide variety of syntax groups are used but
they all link by default to railsMethod.

						*rails-syntax-assertions*
If you define custom assertions in test_helper.rb, these will be highlighted
in your tests.  These are found by scanning test_helper.rb for lines of the
form "  def assert_..." and extracting the method name.  The railsUserMethod
syntax group is used.  The list of assertions can be refreshed with
|rails-:Rrefresh|.

PROJECTIONS		*rails-config/projections.json* *rails-projections*

The bulk of rails.vim features support core Rails conventions and a just a
handful of popular additions (such as RSpec).  Projections let you teach
rails.vim about app specific and gem specific behavior.

There are four primary ways to define projections:

1. Globally, in |g:rails_projections|.
2. Per app, in config/projections.json.
3. Per bundled gem, in |g:rails_gem_projections| (requires bundler.vim).
4. Inside a bundled gem, in lib/rails/projections.json (requires bundler.vim).

Vim syntax looks a lot like JSON, but with funky |line-continuation|:
>
	let g:rails_projections = {
	      \ "app/uploaders/*_uploader.rb": {
	      \   "command": "uploader",
	      \   "template":
	      \     ["class {camelcase|capitalize|colons}Uploader < "
	      \      . "CarrierWave::Uploader::Base", "end"],
	      \   "test": [
	      \     "test/unit/{}_uploader_test.rb",
	      \     "spec/models/{}_uploader_spec.rb"
	      \   ],
	      \   "rubyMacro": ["process", "version"]
	      \ },
	      \ "features/support/*.rb": {"command": "support"},
	      \ "features/support/env.rb": {"command": "support"}}

Keys can be either literal file names or globs containing a single asterisk.
In the latter case, you can use {} placeholders in the values to plug in some
transformation of the variable portion, based on those available in
projectionist.vim.  See projectionist.vim's documentation for a comprehensive
explanation, but you can probably get the gist from the list below.

Older versions of rails.vim used the following unsupported % expansions, shown
here with their {} equivalents:

`%s`: `{}` (Original)
`%S`: `{camelcase|capitalize|colons}` (Ruby class name)
`%S`: `{camelcase|capitalize|dot}` (JavaScript class name)
`%p`: `{plural}`
`%i`: `{singular}`
`%h`: `{underscore|capitalize|blank}`

The full list of available options is as follows:

						*rails-projection-alternate*
"alternate" ~
	Determines the destination of the |rails-:A| command.  If this is a
	list, the first readable file will be used.  For a related file, as
	with :.A and :R, {lnum} and {define} expand to the current line number
	or 'define' match.
						*rails-projection-related*
"related" ~
	Deprecated in favor of "alternate" with either a {lnum} or {define}.
	Use {lnum|nothing} to force a file not to match a plain :A without
	interpolating anything.
						*rails-projection-test*
"test" ~
	Determines the default test file to run with |:Rails| and
	|rails-:Runner|.  Also serves as a default for "alternate".
						*rails-projection-task*
"task" ~
	Determines the default rake task to run.  Provide {lnum} or {define}
	to substitute the current line number or 'define' match (typically a
	method), or just a bare % (like |:_%|) to substitute the current file
	name.
"keywords" ~
	Obsolete: see rubyMacro, rubyAction, and rubyHelper below.
						*rails-projection-command*
"command" ~
	Names a navigation command to be created.  Use the same name on
	multiple projections to combine them into a single command.  Glob
	keys are used when the command is given an argument, and literal file
	keys are used when no argument is given.  See the "features/support"
	entries above for an example :Esupport that defaults to env.
						*rails-projection-affinity*
"affinity" ~
	Provide this if the root of your file name corresponds to either
	a model or controller.  The root of a helper generally corresponds to
	a controller, for example, so a "helper" projection would have an
	"affinity" of "controller".  You can also provide "collection" if it
	corresponds to a plural model (e.g., fixtures), or "resource" if it
	corresponds to a singular controller.  Providing this lets you use
	other affiliated commands without an argument, and determines the
	default if a command has no literal file name.
						*rails-projection-template*
"template" ~
	If you provide a ! after the argument to the navigation command (that
	is, :Euploader foo!, NOT :Euploader! foo), and a new file is created,
	this will be used as an array of lines to populate the body.
						*rails-projection-railsParams*
"railsParams" ~
	Provides a dictionary of defaults for URL parameters for
	|rails-:Preview|, for example {"user_id": "2"}.  The fallback for
	unspecified parameters is "1".
						*rails-projection-compiler*
						*rails-projection-railsRunner*
"railsRunner" ~
	Determines the command (and |:compiler| plugin) to use with
	|rails-:Runner| in lieu of a literal `rails runner`.  Can be
	"minitest", "rspec", or "cucumber".
						*rails-projection-rubyMacro*
"rubyMacro" ~
	List of keywords to highlight as class declarations (like
	before_action or validates_presence_of).
						*rails-projection-rubyAction*
"rubyAction" ~
	List of keywords to highlight as imperative methods (like
	redirect_to or create_table).
						*rails-projection-rubyHelper*
"rubyHelper" ~
	List of keywords to highlight as functional methods (like
	params or any view helper).

CONFIGURATION					*rails-configuration*

In addition to projections (described above) and the crude hammer of global
settings (described below), rails.vim provides a few different mechanisms for
configuration.

					*rails-:autocmd* *rails-autocommands*
If you would like to set your own custom Vim settings whenever a Rails file is
loaded, you can use an autocommand like the following in your vimrc: >

	autocmd User Rails		map <buffer> <F9> :Rails<CR>

There used to be autocommands that fire based on the "type" or file name of
the buffer, but they have been removed.  If you still need to execute code for
certain file types only, use the bare User Rails event above and check
rails#buffer().relative() for the path relative to the Rails root.

						*macros/rails.vim*
If you have several commands to run on initialization for all file types, they
can be placed in a "macros/rails.vim" file in the 'runtimepath' (for example,
"~/.vim/macros/rails.vim").  This file is sourced by rails.vim each time a
Rails file is loaded.

GLOBAL SETTINGS					*rails-global-settings*

When all else fails, set a global.

						*g:rails_ctags_arguments*
Additional arguments to pass to ctags from |:rails-Ctags|.  Defaults to
limiting to Ruby files.
>
	let g:rails_ctags_arguments = ['--languages=Ruby']
<
This option is ignored if a ctags configuration file named .ctags is found in
the root of the project.

						*g:rails_projections*  >
Defines the set of globally available projections.  See |rails-projections|.
Where possible, it is generally advisable to use |g:rails_gem_projections| or
|config/projections.json| instead.

						*g:rails_gem_projections*
This is a dictionary where the keys are gem names and the values are
projection dictionaries.  Projections are only used if the given gem is
bundled (requires bundler.vim).
>
	let g:rails_gem_projections = {
	      \ "active_model_serializers": {
	      \   "app/serializers/*_serializer.rb": {
	      \     "command": "serializer",
	      \     "affinity": "model"}},
	      \ "fabrication": {
	      \   "spec/fabricators/*_fabricator.rb": {
	      \     "command": "fabricator",
	      \     "affinity": "model",
	      \     "alternate": [
	      \       "db/schema.rb#{plural}{lnum|nothing}",
	      \       "app/models/{}.rb"],
	      \     "test": "spec/models/{}_spec.rb",
	      \     "template": "Fabricator :{} do\nend"}}}
<
See |rails-projections|.  Generally, you should prefer these gem projections
over global projections to avoid getting a bunch of useless commands in every
single project.

Gem maintainers may also provide custom projections by placing them in
lib/rails/projections.json.

ABOUT					*rails-about* *rails-plugin-author*

The latest stable version can be found at
	http://www.vim.org/scripts/script.php?script_id=1567

Bugs can be reported and the very latest development version can be retrieved
from GitHub:
	https://github.com/tpope/vim-rails >
	git clone https://github.com/tpope/vim-rails.git
<
						*rails-license*
Copyright (c) Tim Pope.  Distributed under the same terms as Vim itself.
See |license|.

 vim:tw=78:ts=8:ft=help:norl:
