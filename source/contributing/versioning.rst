==================================================
The Sponge Versioning System and Repository Layout
==================================================

With the release for beta we've moved the sponge api versioning to semer (see http://semver.org/).
This change means that every time we're making a release which has non-backwards-compatible
(breaking) changes we have to increment the major version of the api by one (eg. from 3.0.0 ->
4.0.0). The layout of our branches which is described below are designed to assist with being able
to make minor releases without a breaking change forcing us to make it a major release. This branch
layout applies to the SpongeAPI, SpongeCommon, SpongeForge, and SpongeVanilla repositories.

The Core Branches
=================

There are three branches which form the core of our repositories, they are master, bleeding, and
release. The master and bleeding branches are for active development and the release branch tracks
the commit as of the most recent release build.

The key differences between the master and bleeding branches is that any feature branches which are
breaking *must* be merged into the bleeding branch. This allows the master branch to only contain
backwards-compatible changes allowing minor versions to be released based on it if necessary.

Release Branches
================

Prior to releasing builds the content of the release should be first moved to a release branch.
This branch allows dedicated testing to be performed for a release without forcing a code freeze on
the development branches. Any bugfixes applied to the release branch are merged back to the master
branch when the release if finalized. Once a release if made the version of the master and bleeding
branches are both updated, the master branch to the next patch version and the bleeding branch to
the next major version (assuming it was not already on the next major version).

Hotfix Branches
===============

If after a release is made a significant bug is found a hotfix branch can be created based on the
last release version and a new release can be made from this hotfix branch with the patch version
incremented by one. The hotfix can then be merged back into master for included into future versions
as well.

Feature Branches
================

New features or changes will continue to be done in a feature/foo or fix/bar branch. When merging
back into a development branch (master or bleeding) you should consider whether the changes are
breaking or are strictly backwards-compatible. If the changes are purely new features or
binary-compatible bugfixes then the feature branch can be merged into the master branch. If the
changes include any breaking changes however then the feature branch must be merged into the
bleeding branch to be included in the next major release.

https://dl.dropboxusercontent.com/u/17223377/bin/Sponge/sponge-flow.png
