GitAliases
==========

A collection of aliases to support git in bash.

## cd_git_root.alias

A function that overrides the default behaviour of the cd builtin in bash.

When cd is called without arguments, and $PWD is a subdirectory of a git repository, cd will take you to the root of the repository. If cd is already at the root of the repository, and called without arguments cd will behave as it normally does when it is called without arguments. When called with arguments, cd should behave as expected.

### Example

``
aoife@VBox1 ~/git-repos/SampleRepo/src/main/python/lib $ cd
aoife@VBox1 ~/git-repos/SampleRepo $ cd
aoife@VBox1 ~ $ cd git-repos/
aoife@VBox1 ~/git-repos $ ls
GitAliases  SampleRepo
aoife@VBox1 ~/git-repos $ cd ..
``

TODO
====

## General

* Some sort of automated tests would be awesome.
* Testing across other platforms is a Very Nice To Have (some sort of illumos distro, maybe?)

## cd_git_root.alias

* Need a safety check to make sure that other aliases or functions are not overridden.
* Preferably, we need a strategy to delegate to pre-existing overriding versions of cd to other functions before reverting to builtin behaviours.
* The alias currently relies on the behaviour that __gitdir() returns ".git" when $PWD is the top-level directory of the repository, and dirname will then return "." in that circumstance. This behaviour needs to be verified on as many platforms as possible, or make it so we can force dirname to return the full path, so we can reliably compare to $PWD. (I remember a particularly nasty bug in other code, once upon a time, where a shell builtin for dirname returned a relative path when possible, while another's implementation returned the full path, so I'd like to get a consistent behaviour) 
