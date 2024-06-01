obj-m += samsung-galaxybook.o
SRC := $(shell pwd)
MODULE_NAME := samsung-galaxybook
MODULE_VERSION := 0.1
DKMS_MODULE_DIR := /usr/src/$(MODULE_NAME)-$(MODULE_VERSION)

make:
	$(MAKE) -C /lib/modules/$(shell uname -r)/build M=$(SRC) modules

modules_install:
	$(MAKE) -C $(KERNEL_SRC) M=$(SRC) modules_install

dkms_install: make
	sudo mkdir -p $(DKMS_MODULE_DIR)
	sudo cp dkms.conf samsung-galaxybook.c Makefile $(DKMS_MODULE_DIR)
	sudo dkms add -m $(MODULE_NAME) -v $(MODULE_VERSION)
	sudo dkms install -m $(MODULE_NAME) -v $(MODULE_VERSION)

dkms_uninstall:
	sudo dkms remove -m $(MODULE_NAME) -v $(MODULE_VERSION) --all || true
	sudo rm -rf /usr/src/$(MODULE_NAME)-$(MODULE_VERSION)

clean:
	rm -f $(SRC)/*.cmd && \
	rm -f $(SRC)/.*.cmd && \
	rm -f $(SRC)/*.ko && \
	rm -f $(SRC)/*.mod && \
	rm -f $(SRC)/*.mod.c && \
	rm -f $(SRC)/*.o && \
	rm -f $(SRC)/Module.symvers && \
	rm -f $(SRC)/modules.order
