[![MELPA](http://melpa.org/packages/sly-hello-world-badge.svg)](http://melpa.org/#/sly-hello-world)
[![Build Status](https://travis-ci.org/capitaomorte/sly-hello-world.svg?branch=master)](https://travis-ci.org/capitaomorte/sly-hello-world)

# Use this to write a [SLY][sly] contrib

`sly-hello-world` is an external contrib for [SLY][sly] that does
nothing particularly useful. It's just a template for writing other
external contribs.

It makes it easier to setup a SLY extension that:

* is completely self-contained (doesn't need to be bundled with SLY);

* has both Emacs-Lisp and Common-Lisp counterparts

  See `sly-hello-world.el` and `slynk-hello-world.lisp`

* has automated [Travis tests](https://travis-ci.org/capitaomorte/sly-hello-world) already in place

  See the file `.travis.yml`. There are some sample unit tests for
  this contrib using SBCL and CCL there;

* is easily added to [MELPA](http://melpa.org)

  Just make a [pull request to
  MELPA](https://github.com/milkypostman/melpa/pulls) and ask for your
  recipe to be added to `recipes/`. Use this template:

```lisp
(sly-hello-world :fetcher github
                         :repo "capitaomorte/sly-hello-world"
                         :files (:defaults
                                 "*.lisp"
                                 "*.asd"))
```


The remainder of this `README.md` file is itself a template for the
one that should be included in the contrib.

## Quick and easy

Clone this repository somewhere, go to a shell there and type:

```
$ emacs -Q -L <path-to-sly> -l sly-hello-world.el -f sly
```

In `.lisp` files you can now `C-c H W` (or `M-x sly-hello-world`) to
be informed of the hello-worldness of your Lisp.

## Install from MELPA

Perform the [usual MELPA setup](http://melpa.org) and then select
`sly-hello-world` for installation from the package menu or from `M-x
package-install`.

Once it's done, `M-x sly` should now bring up a hello-world enabled
SLY.

## Install from Git

Since this is an external contrib with both Elisp and Lisp parts,
merely loading the Elisp will have little effect. The contrib has to
be registered in SLY's `sly-contribs` variable for SLY to take care of
loading the Lisp side on demand.

For convenience, the `sly-hello-world-autoloads` file takes care
of this automatically. So the following setup in your `~/.emacs` or
`~/.emacs.d/init/el` init file should be enough:

```elisp
;;; regular SLY setup
(setq inferior-lisp-program "/path/to/your/preferred/lisp")
(add-to-list 'load-path "/path/to/sly")
(require 'sly-autoloads)

;;; sly-hello-world setup
(add-to-list 'load-path "/path/to/sly-hello-world")
(require 'sly-hello-world-autoloads)
```

In case you already have SLY loaded and running, you might have to
`M-x sly-setup` and `M-x sly-enable-contrib` to enable it.

[sly]: https://github.com/capitaomorte/sly





