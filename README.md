# LightnCandy-CLI
LightnCandy-CLI is a CLI wrapper around the PHP implementation of mustache/handlebars [LightnCandy](https://github.com/zordius/lightncandy). This CLI tool can be used in your build process to compile mustache/handlebars templates to PHP to be used with the LightnCandy library or on their own.

## Installation
LightnCandy-CLI is meant to be used as a CLI tool and can be globally installed with composer like so:
`composer global require pxlbros/lightncandy-cli`

You can also install LightnCandy-CLI into your project directory and run it straight from the vendor folder if you want to.

## Usage

### Basic
The first and only unamed argument is a path to the template file that you wish to compile.

`$ lightncandy path/to/template.hbs`

If omitted, LightnCandy-CLI will use STDIN as the template. This is usefull because you can pipe input into the utility.

`$ echo 'Hello {{name}}!' | lightncandy`

By default LightnCandy-CLI will pipe the compiled template to STDOUT but you can also write the output to disk by providing a path.

`$ lightncandy path/to/template.hbs -o path/to/output.php`

### LightnCandy Options
LightnCandy supports many flags that can be used to configure how it compiles your templates. A list of these options and what they do can be found on the page for the [LightnCandy](https://github.com/zordius/lightncandy) library. You can toggle them like so:

`$ lightncandy path/to/template.hbs --FLAG_BARE --FLAG_HANDLEBARSJS`

You can also use `$ lightncandy --help` to see a list of availible options and their descriptions in your command line.

### Other Options

#### basedir
`-b/--basedir "path/to/partials/directory/ path/to/different/dir"`
Space seperted list of directory paths containing partial templates.

#### helpers
`-p/--helpers "path/to/helpers/directory/ path/to/different/dir"`
Space seperated list of directory paths containing helper functions.

#### blockhelpers
`-k/--blockhelpers "path/to/blockhelpers/directory/ path/to/different/dir"`
Space seperated list of directory paths containing block helper functions.

#### hbhelpers
`-h/--hbhelpers "path/to/hbhelpers/directory/ path/to/different/dir"`
Space seperated list of directory paths containing handlebars style helper functions.

#### fileext
`-e/--fileext ".tmpl .partial"`
Space seperated list of file extensions for template files.

#### render
`-r/--render`
If provided, will run the compiled template and will output the result instead.

#### data
`-d/--data`
JSON string to pass to the rendering function if the render flag is provided.
