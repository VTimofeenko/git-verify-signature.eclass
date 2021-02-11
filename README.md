This repo contains an eclass that may be used to verify the signature on the top commit of a repository checked out during `git-r3` based installation.

git-verify-signature.eclass is based on [`verify-sig.eclass`](https://gitweb.gentoo.org/repo/gentoo.git/tree/eclass/verify-sig.eclass).

# Usage

This eclass relies on same variables as `verify-sig` eclass. The simplest use case is installing a live ebuild. To verify the signature, add the following to your ebuild:

* Add `inherit git-verify-signature`
* Specify the key location in `VERIFY_SIG_OPENPGP_KEY_PATH`
* Add BDEPEND dependency to the openpgp-key ebuild

When a user would be installing that ebuild with `verify-sig` useflag, the default `src-unpack` from `git-verify-signature.eclass` will run the `git-r3.eclass`'s standard `src_unpack` and verify the top signature.

The function to verify the signature is available separately as `git-verify-signature_verify-commit` in case non-default `src_unpack` is needed.

See [vtimofeenko-zshrc ebuild](https://github.com/VTimofeenko/weaveworld-overlay/blob/main/app-shells/vtimofeenko-zshrc/vtimofeenko-zshrc-9999.ebuild) for example.

Also see the code example inside the eclass.

# Installation

Add as a submodule to your overlay if using git and symlink the git-verify-signature.eclass file to `eclass` directory.

# Example

See [weaveworld-overlay](https://github.com/VTimofeenko/weaveworld-overlay)
