* Security - what made up the build - bad compiler/flags/
   * SLSA: Was the artifact built from the expected process and sources? For example, Python package "pyyaml" is supposed to be built from https://github.com/yaml/pyyaml using (say) GitHub Actions workflow "build.yaml" in that repo. If I download an artifact with a given hash, reject if it was not built from that source and process.
   * Bad builder: TravisCI is compromised, I want to find all artifacts in my organization that used builder during the relevant time window so that I can replace them with fixed artifacts
   *  Bad compiler/flags (Brandon to fill this in) - defer for later in SPDX 3.x if the usecase is asked for
	* In this case, the usage of a bad version of binutils led to certain artifacts having the inappropriate ownership when used in a build (https://lists.archlinux.org/archives/list/arch-dev-public@lists.archlinux.org/thread/WSXBKO2PHIHHXN3YK7H54PFKJS6PQGHV/), this may trigger the question of which binaries were affected.
* Reproducibility (SPARQL queries, <https://reproducible-builds.org/>)
  * Allow someone else to reproduce the build (called "buildinfo" in reproducibile builds community) given just the SPDX Package element and access to the relevant sources and dependencies. Value add would be a generic buildinfo. Right now (e.g. Debian) the build command and environment are assumed (e.g. dpkg-buildpackage).
  * Show evidence of reproducibility: two different builds produced the same output. May be criteria for a customer.
  * Find cases of non-reproducible behavior: where there multiple builds that ran the same process on the same inputs but got the same output
* Auditing quality / pedigree of build
  * Compiler environment used to generate the build (for example stack protection enabled)
  * Most build systems don't say what they used, they just output the binary
* Licensing; whether specifically licensed source made it into the output
  * Licensing profile in draft (not in scope right now but should address in the future)
  * Requries file level access to what was used to be built
* Safety
  * https://www.linux.com/featured/sboms-supporting-safety-critical-software/
