.PHONY: help rpm deb clean

help:
	@echo "Possible make targets: deb, rpm, clean"

VERSION=2015.03

nqp-$(VERSION).tar.gz:
	wget http://rakudo.org/downloads/nqp/nqp-$(VERSION).tar.gz

download-nqp: nqp-$(VERSION).tar.gz

DEBUILD_DIR=/tmp/nqp_debuild
deb: download-nqp
	if [ -d $(DEBUILD_DIR) ]; then rm -r $(DEBUILD_DIR); fi
	mkdir -p $(DEBUILD_DIR)
	cp nqp-$(VERSION).tar.gz $(DEBUILD_DIR)/nqp_$(VERSION).orig.tar.gz
	tar -C $(DEBUILD_DIR) -xvzf $(DEBUILD_DIR)/nqp_$(VERSION).orig.tar.gz
	cp -r debian $(DEBUILD_DIR)/nqp-$(VERSION)/
	cd $(DEBUILD_DIR)/nqp-$(VERSION)/debian; debuild -us -uc
	@echo "Now check the .deb file in $(DEBUILD_DIR)"

clean:
	rm -rf $(DEBUILD_DIR)
