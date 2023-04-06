# Heroku image optimizers buildpack

This buildpack will provide the following image optimizer binaries to your Heroku app:

- `advpng`
- `gifsicle`
- `jpegoptim`
- `jpegtran`
- `optipng`
- `pngcrush`
- `pngquant`
- `cwebp`
- `dwebp`

This buildpack supports the following Heroku [stacks](https://devcenter.heroku.com/articles/stack):

- [heroku-20](https://devcenter.heroku.com/articles/heroku-20-stack)
- [heroku-22](https://devcenter.heroku.com/articles/heroku-22-stack)

During compile time of this buildpack the following steps will be done:

- Detect the current used `stack`
- Copy the binaries in the folder `vendor/optimizers` inside the `$BUILD_DIR`
- Symlinks to the binaries will be added to ensure that possible following buildpacks will have these binaries available
- The path `vendor/optimizers` will be added to the `PATH` environment through the `optimizers.sh` script which is
  located in the `.profile.d` folder
- At the end the version of each binary is displayed

## Installation/Usage

To use this buildpack you can add it by multiple ways to your Heroku app. Please see the Heroku
[documentation](https://devcenter.heroku.com/articles/buildpacks#using-a-third-party-buildpack) for further information.
