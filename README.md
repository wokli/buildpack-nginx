# Dokku Buildpack: nginx

This is the official dokku buildpack for static websites, powered by nginx.

## Usage

All static files that you want to serve should be in the root directory of your repository. No need to use a seperate `www` folder. `buildpack-nginx` will automatically download the buildpack, download NGINX, compile it, and install it. The next time you push your project, the buildpack will reuse the precompiled binaries.

### Dokku

To trigger detection of this buildpack in Dokku, you have two options:

- Automatic: Add an *empty* file called `.static` to your root directory of your web project.
- Manual: Set your `BUILDPACK_URL` via `dokku config:set BUILDPACK_URL=https://github.com/dokku/buildpack-nginx.git`

### Heroku

Heroku users can use this buildpack by running the following command:

```
heroku buildpacks:set https://github.com/dokku/buildpack-nginx.git
```

## Configuration

You can override the nginx root via setting the `NGINX_ROOT` environment variable. This should be a relative path in your repository.

You may completely override the built-in nginx config by placing an `nginx.conf.erb` file in the root, modeled after our own [`conf/nginx.config.erb`](https://github.com/dokku/buildpack-nginx/blob/master/conf/nginx.conf.erb). This will be used inside of the container, and not by the host Dokku instance.

## Credits and License

`buildpack-nginx` is licensed under the CC0 1.0 Universal license and has been informed by many similar projects on the web.

[Florian Heinemann](http://twitter.com/TheSumOfAll/)
