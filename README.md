[![Build Status](https://travis-ci.org/geneontology/contributor-data-pool.svg)](https://travis-ci.org/geneontology/contributor-data-pool)

# contributor-data-pool

Contributor data pool: an experimental freestanding structured resource for external data contributors

# Overview

The purpose of this repository is to provide a template for external
data contributors to the Gene Ontology Consortium (GOC). By either
forking the provided template or by creating a data resource (on
GitHub or otherwise) that follows the same conventions, an external
data provider (individual or group) can easily create a resource that
could potentially be consumed by the GOC.

This approach is somewhat inspired by what has been done with NPM,
trying to find a minimal freestanding layout that can be extended to
meet specific needs. The absolute minimum would be a YAML file
describing the data and a named directory containing the data. Beyond
that, there are a multitude of optional fields describing licensing,
contributors, upstream or associated data sets (which, if they have the
same format, can be crawled), etc. The main firm spot is the naming of
the data directories to essentially map onto known formats. All other
directories can be used by resource maintainers for whatever they
need, including extending the YAML data pool description in
non-conflicting ways.

This offers many advantages over trying to centralize the effort onto
current resource: easier-self help, distribution of effort, simpler to
port and/or integrate with current systems, etc.

For people who just wanted to contribute data and do the least amount
of work possible, or had the least resources, they could fork our
template repo and just and it, commit. As part of the default forks,
there are CI tests ((soon) GitLab and GitHub) which not only let you
know if they got the spec right, but leaves open the possibility to
have a "call home" for some simple analytics, and give us the ability
to proactively approach interested groups. There are a rich set of
defined fields (e.g.: what tools is this data for? what publications
is this from?) for people who wanted to dig in more. As part of the
template, we intend to include a "completeness grade", to help
encourage discovery and usability, but tools should always work with
the minimum.

Included in this, providing the correct setup (to be detailed later), 

# Resource Layout

The absolute minimum needed is the following directory structure available at a URL:

```
pool.yaml
DATADIR/
DATADIR/datafile
```

where "DATADIR" is a directory name defined in pool.yaml (see below).

The top-level directory "_goc/" should not be used.

# pool.yaml

* name (required)
* identifier (required)
* comment (optional)
* contacts (list, optional)
* about (list, optional)
* description (required)
* data-pools (list, required)
** format (required)

⋅⋅⋅One of a set of "registered" data types recognized by the GOC. This may include "gaf-2.0", etc.

** path (required)
* comment (optional)
** contributors (list, optional)

⋅⋅⋅A list of identified contributors.

** upstream (list, optional)
** refresh (optional)

⋅⋅⋅A hint about how often you will refresh the data.

This list is currently very much in flux and will be revised.

# Letting us know

Besides the act of creating a freestanding data resource, you should
definitely let us know about it. If you have forked this repo or used
some of our tools, that may give us some idea of who you are, the best
way for us to have a dialog about your data is if you contact us at
TBD.

While the care and upkeep of your data is yours, the GOC would like to
coordinate these repos (who is on our pipeline list and who is not,
who we are grooming, so on) and give feedback. This coordination is
still TBD, but could very easily be folded into the current Drupal
site.

# Roadmap

Implied in all this is that our tools (loaders, etc.) should have to
have at least basic support for working with these pools. Given how
simple it should be, I don't think it would be much of an effort and
can be approached slowly--the initial format is for external groups
trying to get their data in, but eventually it's good form to eat
one's own dog food.

Exposing data resources in this manner would likely have uses outside
of the Gene Ontology Consortium.

Following this, we can also start to see how this might thread into
better mechanisms for data attribution.

## License

The software in this repository is help under the 3-clause BSD license.

The documentation in this repository in held under CC0.
