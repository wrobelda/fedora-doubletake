.PHONY: srpm

srpm:
	dnf -y install rpm-build rpmdevtools rpmautospec git-core go-srpm-macros go-vendor-tools golang python3-specfile
	mkdir -p "$(outdir)"
	spectool -g -S doubletake.spec
	go_vendor_archive create --config go-vendor-tools.toml doubletake.spec
	sha512sum --check sources
	rpmautospec process-distgit "doubletake.spec" "$(outdir)/doubletake.spec"
	rpmbuild -bs "$(outdir)/doubletake.spec" --define "_sourcedir $(CURDIR)" --define "_srcrpmdir $(abspath $(outdir))"
