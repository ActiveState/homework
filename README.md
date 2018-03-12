Thank you for your interest in working with ActiveState as a developer. This
programming assignment will help us to evaluate your skills relative to our
working environment and is used as a primary tool in our hiring process. Later
on in the hiring process we will have one of our developers pair with you on
making changes to your code, fixing bugs, etc.

We expect this assignment to occupy no more than 3 hours of your time.  We are
primarily looking for high-quality code, including test code, and we recognize
that you may not have time to fully polish your work, so focus on code before
documentation and other niceties.

We strongly encourage the use of third party packages as you work on this
assignment. However, see the note at the end about providing us with
instructions on installing/running your assignment.

We are also happy to accept solutions provided in the following languages:

* Go
* JavaScript
* Perl
* PHP
* Python
* Ruby

If you would like to use a different language, please contact us before
continuing with this assignment.

## Requesting an Exemption

The purpose of this assignment is to help us better understand your abilities
as a software engineer. In addition, we will also use the work you produce as
part of a pairing session during our hiring process.

You may already have some publicly available code which would help us on both
these fronts. If you do, let us know and we will take a look. We’re looking
for something with the following characteristics:

* This must be your project, meaning that you wrote most of the code and you
  are a primary maintainer.
* It should be something that is neither trivially small nor overwhelmingly
  large. We’re looking for something that ranges from 500-2000(ish) lines of
  code. Anything much smaller won’t have enough complexity for us to evaluate
  your engineering skill. Anything much larger is just overwhelming for us to
  evaluate and pair with you on.
* There should be something in the project that you’d like to work on during a
  pairing session. This could be fixing a bug, adding a small feature, doing a
  refactoring, adding tests, etc. We don’t have to finish this work during the
  session, but it should be something simple enough that we can really dig
  into it in the space of 90 minutes.

Please let your recruiting contact at ActiveState know if you have something
you think is appropriate. We'll get back to you promptly to let you know if it
is, in which case you can skip the homework assignment entirely.

## Assignment

We have provided some sample data in the form of the `META.json` files that
accompany most Perl libraries uploaded to CPAN. See
https://metacpan.org/pod/CPAN::Meta::Spec for documentation on this format.

For this assignment, the only important key in this metadata is the
**prereqs** key.

The files are located under `data/` in a directory tree where each
subdirectory corresponds to the name of a Perl distribution, like “DateTime”,
"Eval-Closure", or "Module-Runtime".

There are also some additional support files under `data/`. The first is a
`data/module-distro-map.json` that maps Perl module names to Perl distribution
names. Note that the `META.json` files belong to a distribution (distro), but
the prereqs themselves always specify individual modules. A distro can contain
one or more modules. This means you will need to translate from module names
to distro names when you are constructing your dependency tree.

All of the files you need are in the `data/` directory. You should not need to
fetch additional data from CPAN or anywhere else on the Internet.

The other is a `data/core-modules.json` file. This contains an array of
modules which are shipped with the Perl core.

Your assignment requires reading this metadata and producing fully resolved
dependency trees.

In the metadata, dependencies are defined by phase ("runtime", "test", etc.)
and by relationship ("requires", "recommends", "suggests").

We are only interested in "runtime" and "test" phase dependencies where the
relationship is "requires". You can ignore everything else.

### The Program

You will write a command line program that accepts the following command line
arguments:

* `--name` - The name of a distribution for which dependencies should be
  resolved. May be specified more than once.
* `--text` - By default, output will be as JSON but when this flag is passed
  the output should be some sort of human-readable tree representation.

The JSON output for dependency tree should look like this:

```json
{
    "DateTime": {
        "runtime": {
            "DateTime-Locale": {
                "runtime": {
                    "Params-ValidationCompiler": {
                        "runtime": { "..." },
                        "test": { "..." },
                    },
                    "..."
                },
                "test": { "..." }
            }
        },
        "test": {
            "CPAN-Meta-Check": { "..." }
        }
    },
    "..."
}
```

In other words, you should completely resolve the dependency tree for all
runtime and test prereqs. That means some distros may appear more than once in
the tree. However, circular dependencies are an error, and you can handle them
by printing an error and exiting.

If a **module name (not a distro name)** appears in the list of core modules
in `data/core-modules.json` then you can omit it from the output entirely. You
can also ignore version numbers for the purposes of this assignment.

You can also ignore "perl" as a prereq. (This specifies the minimum version of
Perl that a distro needs.)

If a particular distro has no dependencies, represent it as an empty object in
the JSON.

In `--text` mode, pick a representation of the output that you like. This can
be any sort of plain text, including Markdown, ASCII art, etc.

### Instructions for Us

If your solution requires the installation of additional libraries, packages,
etc., please provide details on how we should do this in order to run your
code.  Assume that we will be running this code on an Ubuntu Linux system. If
you can provide a Dockerfile with your solution, that is a plus.

Do not assume that we have expertise with the language you have chosen for
your implementation, unless that language is Perl or Go.

## Sharing Your Code with Us

We do not want your answer available on the public Internet. **Do not put this
code into a public repo in order to share it with us.**

You can share it with us in one of two ways:

* Make a private repo and share it with us. You should have already been told
  who to invite if we asked you do this homework.
  * Note that while GitHub charges for private repos, BitBucket and GitLab
    both offer private repos as part of their free plans.
* Send an email containing a zip or tarball attachment. You can send this to
  your recruiting contact at ActiveState.

## Copyright

This repository is copyright ActiveState Software, Inc. 2018. You may
distribute it under the [Attribution-ShareAlike 4.0
International](https://creativecommons.org/licenses/by-sa/4.0/).
