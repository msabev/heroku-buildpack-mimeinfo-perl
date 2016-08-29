# heroku-buildpack-mimeinfo-perl

This repository is a fork of [heroku-buildpack-apt](https://github.com/heroku/heroku-buildpack-apt). It's a Heroku buildpack that is required by [scinote-web](https://github.com/biosistemika/scinote-web) (which uses `mimetype` script) to run properly on Heroku.

The buildpack installs the **MimeInfo** Perl library into the Heroku container.

## Changes

The buildpack is very similar to the original, there are just couple of changes:
* in [detect](/bin/detect), there is no checking for `Aptfile` (buildpack always succeeds),
* in [compile](/bin/compile), required libraries that should be installed via `apt-get` are simply declared in a `$packages` variable, and additional environmental variables are declared towards the end of the file.

## Usage

To add this buildpack to Heroku app, simply run the following command:
```
heroku buildpacks:add --index <index> https://github.com/biosistemika/heroku-buildpack-mimeinfo-perl.git -a <app>
```
Where `<index>` is a 1-based index where the buildpack should be added (e.g. if you already have 2 buildpacks for your app, this index would have value 3 to be appended to the end), and `<app>` is the name of your Heroku app.

## License

MIT
