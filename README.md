This repo contains an eclass that may be used to verify the signature on the top commit of a repository checked out during `git-r3` based ebuild installation.

# Usage

This eclass relies on same variables as [`verify-sig.eclass`](https://gitweb.gentoo.org/repo/gentoo.git/tree/eclass/verify-sig.eclass) eclass. The simplest use case is installing a live ebuild. To verify the signature, add the following to your ebuild:

* Add `inherit git-verify-signature`
* Specify the key location in `VERIFY_SIG_OPENPGP_KEY_PATH`
* Add BDEPEND dependency to the openpgp-key ebuild

When a user would be installing that ebuild with `verify-sig` useflag enabled, the default `src-unpack` from `git-verify-signature.eclass` will run the `git-r3.eclass`'s standard `src_unpack` and verify the signature on top commit.

The function to verify the signature is available separately as `git-verify-signature_verify-commit` in case non-default `src_unpack` is needed.

See [vtimofeenko-zshrc ebuild](https://github.com/VTimofeenko/weaveworld-overlay/blob/main/app-shells/vtimofeenko-zshrc/vtimofeenko-zshrc-9999.ebuild) for example.

Also see the code example inside the eclass.

# Installation

Download the [latest release from GitHub](https://github.com/VTimofeenko/git-verify-signature.eclass/releases) and copy the `
git-verify-signature.eclass` file to your overlay's eclass directory.

Alternatively, install the latest `app-portage/git-verify-signature` from [nitratesky overlay](https://github.com/VTimofeenko/nitratesky) and copy the file from ebuild's message.

# Example

See [weaveworld-overlay](https://github.com/VTimofeenko/weaveworld-overlay)

# Credits

The author would like to express his thanks to the participants of [the thread at Gentoo forums](https://forums.gentoo.org/viewtopic-t-1129590.html), specifically to Alexey Mishustin (halcon).
