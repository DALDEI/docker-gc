
.PHONY: rpm

rpm:
	mkdir -p BUILDROOT/
	rpmbuild \
		--define "_topdir `pwd`" \
		--define "_sourcedir %{_topdir}/.." \
	    -ba ./docker-gc.spec
clean:
	rm -rf BUILD BUILDROOT RPMS SPECS SRPMS *~
