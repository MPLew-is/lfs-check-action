# LFS Check Action #

This action is an incredibly lightweight reusable workflow to validate that all [Git LFS](https://git-lfs.github.com) files registered in your repository's `.gitattributes` configuration are actually LFS pointers.
This can catch scenarios where a user adds a raw binary file into the git history, eliminating the benefits of LFS for those files and causing warnings/errors for users with LFS enabled.

This action is literally just a wrapper around the following steps:
1. Check out the repository
	- Also, don't actually download LFS file contents, since we're just validating the LFS pointers
2. Run `git lfs fsck --pointers` to validate all registered files are actually LFS pointers


## Quick start ##

Add to a workflow in your repository:
```yaml
...
    steps:
      - uses: MPLew-is/lfs-check-action@1
```

That's it - this action takes no inputs and returns no outputs, only returning a status code about whether the LFS validation succeeded.
