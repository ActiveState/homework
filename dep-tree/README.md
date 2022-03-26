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

We are happy to accept solutions provided in the following languages:

* Go
* Java
* JavaScript
* Perl
* Python
* Ruby

If you would like to use a different language, please contact us before
continuing with this assignment.

## Time Limit

We'd like you to complete this assignment within one week of receiving
instructions to do this from your recruiting contact, unless you were told
otherwise. However, we understand that this may not always be possible, for
any number of reasons. If this poses a problem for you, please let your
recruiting contact know what timeline works for you.

## Requesting an Exemption

The purpose of this assignment is to help us better understand your abilities
as a software engineer. In addition, we will also use the work you produce as
part of a pairing session during our hiring process.

You may already have some publicly available code which would help us on both
these fronts. If you do, let us know and we will take a look. We’re looking
for something with the following characteristics:

* This must be your project, meaning that you wrote most of the code and you
  are the project's primary maintainer.
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

This data does not contain circular references and you do not need to handle
those in your program.

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

We are only interested in "runtime" phase dependencies where the relationship
is "requires". You can ignore everything else.

### The Program

You will write a command line program that accepts the following command line
arguments:

* `--name` - The name of a distribution for which dependencies should be
  resolved. May be specified more than once.

The program should output a single JSON object to `stdout`. That JSON object
should look like this:

```json
{
    "DateTime": {
        "DateTime-Locale": {
            "Params-ValidationCompiler": {
                "..."
            }
        }
    },
    "..."
}
```

The object's keys are distribution names and the values are in turn objects
where the keys are distribution names. You should completely resolve the
dependency tree for all runtime prereqs. That means some distros may appear
as an object key more than once.

If your program is given multiple `--name` flags you should still produce a
single JSON object. Each of the distro names given on the command line should
be a top-level key in the JSON object you produce.

If a **module name (not a distro name)** appears in the list of core modules
in `data/core-modules.json` then you can omit it from the output entirely. You
can also ignore version numbers for the purposes of this assignment.

You can also ignore "perl" as a prereq. (This specifies the minimum version of
Perl that a distro needs.)

If a particular distro has no dependencies, represent it as an empty object in
the JSON.

#### Example Output for Testing

The `Package-Stash` distribution has a small dependency tree, consisting of
the following:

* Package-Stash
  * B
  * Carp
  * Dist::CheckConflicts
    * Carp
    * Exporter
    * Module::Runtime
      * perl
    * base
    * perl
    * strict
    * warnings
  * Getopt::Long
  * Module::Implementation
    * Carp
    * Module::Runtime
      * perl
    * Try::Tiny
      * Carp
      * Exporter
      * constant
      * perl
      * strict
      * warnings
    * strict
    * warnings
  * Scalar::Util
  * Symbol
  * constant
  * perl
  * strict
  * warnings

**This is the entire dependency tree for `Package-Stash` as modules, not
distributions. Note that this example includes both "perl" and modules shipped
with the Perl core.**

The terminal nodes do not have any dependencies of their own. You can use this
to evaluate the output of your program.

### Instructions for Us

If your solution requires the installation of additional libraries, packages,
etc., please provide details on how we should do this in order to run your
code.  Assume that we will be running this code on an Ubuntu Linux system
(Trusty or Xenial). If you can provide a Dockerfile with your solution, that
is a plus.

Do not assume that we have expertise with the language you have chosen for
your implementation.

Include instructions on how to run your solution either in a `README` file of
some sort or as the output of a `your-solution --help` flag. Your instructions
should tell us how to specify the location of the data directory and how to
specify the distro name(s) to look for.

## Sharing Your Code with Us

Please upload a zip or tarball attachment to our recruiting system.

We do not want your solution available on the public Internet. **Do not
put this code into a public repo in order to share it with us.**
