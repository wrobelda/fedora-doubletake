.PHONY: srpm

srpm:
	dnf -y install rpm-build rpmdevtools rpmautospec git-core go-srpm-macros
	mkdir -p "$(outdir)"
	spectool -g -S doubletake.spec
	sha512sum --check sources
	rpmautospec process-distgit "doubletake.spec" "$(outdir)/doubletake.spec"
	rpmbuild -bs "$(outdir)/doubletake.spec" --define "_sourcedir $(CURDIR)" --define "_srcrpmdir $(abspath $(outdir))"
