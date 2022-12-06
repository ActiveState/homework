Thank you for your interest in working with ActiveState as a data pipeline
developer. This assignment will help us to evaluate your skills relative
to our working environment and is used as a primary tool in our hiring
process. Later on in the hiring process we may have one of our developers
pair with you on making changes or enhancements to your work.

We expect this assignment to occupy no more than 3 hours of your time.
We are primarily looking for high-quality design and documentation
and we recognize that you may not have time to fully polish your work,
so focus on design before other niceties.

If you would like to use a different format or tool, please contact us before
continuing with this assignment.

## Time Limit

We'd like you to complete this assignment within one week of receiving
instructions to do this from your recruiting contact, unless you were told
otherwise. However, we understand that this may not always be possible, for
any number of reasons. If this poses a problem for you, please let your
recruiting contact know what timeline works for you.

## Requesting an Exemption

The purpose of this assignment is to help us better understand your
abilities as a data engineer. In addition, we may also use the work you
produce as part of a pairing session during our hiring process.

You may already have some publicly available work which would help us on both
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

In this assignment, you will analyze and evaluate structured data to propose a
data design that allows us to store, query, and retrieve useful information. For
this example, we will use dependency information for one of the languages we
support.

We have provided some sample data in the form of the `META.json` files that
accompany most Perl libraries uploaded to CPAN. See
https://metacpan.org/pod/CPAN::Meta::Spec for documentation on this format.

This data does not contain circular references and you do not need to handle
those in your assignment.

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

In the metadata, dependencies are defined by phase ("runtime", "test", etc.)
and by relationship ("requires", "recommends", "suggests").

Your task is to propose a database schema to house this data which allows
for efficient execution of the following types of queries:

* given a distro name and a phase, return the graph which represents
  the dependency closure of that distro for that phase.
* given a distro name and a phase, return a list of distros that depend
  on the given distro directly in that phase

Explain how these queries might be structured, in SQL or otherwise,
and how the schema facilitates their efficient execution.

Should time permit, consider that the build phase dependency closure
of a given distro contains the distros that are direct build phase
dependencies of the given distro and the runtime phase closure of
dependencies of those distros.  This is because when building a given
distro a build system will need to run the direct build dependencies
of that distro, not build them.

We are happy to accept solutions in the form of ERD/ERMs or DDL.

## Sharing Your Code with Us

Please upload a zip or tarball attachment to our recruiting system.

We do not want your solution available on the public Internet. **Do not
put this code into a public repo in order to share it with us.**
