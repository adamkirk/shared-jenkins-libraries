# shared-jenkins-libraries

Contains shared jenkins scripts to keep things in the pipelines DRY.

## Structure

Please see: https://jenkins.io/doc/book/pipeline/shared-libraries/

This document explains the structure of this project and outlines how you
should structure any groovy files dependent on the intended behaviour.

 ## Usage

The above document also explains how the library can be used inside a pipeline.
This library is currently implicitly loaded meaning you can use anything defined
in here without having to add any extra import directives etc.

## Developing

Jenkins should be setup to point at a particular commit/branch by default. This
should be overridable inside of a pipeline (i.e. Jenkinsfile), to allow us to
push new versions without breaking existing pipelines.

Any change that 'may' (use your judgement) break an existing pipeline when
published should be rolled out to each pipeline individually to ensure there
are no breaking changes.

Once this has been validated a Jenkins administrator can update the default
commit/branch that jenkins will load. After this any Jenkinsfiles that were
changed during testing should be reverted to point at the default branch.
This is just to ensure we aren't using outdated versions of scripts in
pipelines to save us headaches in the future.

### README

While developing scripts/classes etc it would be beneficial to incude a README
to explain the following points:

- Usage: Any arguments and their default values, and how to use it.
- Summary: An explanation of what this particular script solves; why we need it.

_In the case of the vars directory, this information should be in a file named
identically to the script, but with a .txt extension. i.e. given the function 
vars/someFunc.groovy is defined, there should be a vars/someFunc.txt file also._