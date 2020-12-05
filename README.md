## Fork notes

This is a fork. I don't expect my code to be merged back however if you want, 
you are free to do so.

Changes:

* Nginx's `X-Accel-Redirect`
* Add "Batch Download" permission.
* UI Changes
  * Updated the logo to "Filehub"
  * <kbd>Ctrl</kbd>-<kbd>f</kbd> will not hijack browser's find functionality.
  * <kbd>ESC</kbd> to exit edit/preview;
  * ~~Single-click to open instead of double~~ Using upstream implementation.

### Nginx proxy

When running behind NGINX Proxy, you can also specify "--nginx-accel-path"
to let nginx serve static files; for example, you can specify:

    --nginx-accel-path "/fast-download"

and with in your config file:

```nginx
    location /fast-download {
        internal;
        sendfile on;
        # Other optimisations:
        # https://docs.nginx.com/nginx/admin-guide/web-server/serving-static-content/#optimizing-performance-for-serving-content
        alias /path/to/root;
    }

    root /path/to/frontend/dist;
    location / {
        try_files $uri @filebrowser;
    }

    location @backend {
        proxy_pass ...;
        ...
    }
```

---

<h2 style="text-align: center">
  <img alt="logo" src="https://cdn.jsdelivr.net/gh/jixunmoe-go/filebrowser@84ecca45defb77fb956d0ea2b7eafdbca6053abf/frontend/public/img/logo.svg" width="200"/><br>Filehub (A "File Browser" fork)
</h2>

![Preview](https://user-images.githubusercontent.com/5447088/50716739-ebd26700-107a-11e9-9817-14230c53efd2.gif)

[![Travis](https://img.shields.io/travis/com/filebrowser/filebrowser.svg?style=flat-square)](https://travis-ci.com/filebrowser/filebrowser)
[![Go Report Card](https://goreportcard.com/badge/github.com/filebrowser/filebrowser?style=flat-square)](https://goreportcard.com/report/github.com/filebrowser/filebrowser)
[![Documentation](https://img.shields.io/badge/godoc-reference-blue.svg?style=flat-square)](http://godoc.org/github.com/filebrowser/filebrowser)
[![Version](https://img.shields.io/github/release/filebrowser/filebrowser.svg?style=flat-square)](https://github.com/filebrowser/filebrowser/releases/latest)
[![Chat IRC](https://img.shields.io/badge/freenode-%23filebrowser-blue.svg?style=flat-square)](http://webchat.freenode.net/?channels=%23filebrowser)

filebrowser provides a file managing interface within a specified directory and it can be used to upload, delete, preview, rename and edit your files. It allows the creation of multiple users and each user can have its own directory. It can be used as a standalone app or as a middleware.

## Features

Please refer to our docs at [https://filebrowser.org/features](https://filebrowser.org/features)

## Install

For installation instructions please refer to our docs at [https://filebrowser.org/installation](https://filebrowser.org/installation).

## Configuration

[Authentication Method](https://filebrowser.org/configuration/authentication-method) - You can change the way the user authenticates with the filebrowser server

[Command Runner](https://filebrowser.org/configuration/command-runner) - The command runner is a feature that enables you to execute any shell command you want before or after a certain event.

[Custom Branding](https://filebrowser.org/configuration/custom-branding) - You can customize your File Browser installation by change its name to any other you want, by adding a global custom style sheet and by using your own logotype if you want.

## Contributing

If you're interested in contributing to this project, our docs are best places to start [https://filebrowser.org/contributing](https://filebrowser.org/contributing).
