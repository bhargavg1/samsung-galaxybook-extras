obj-m += samsung-galaxybook.o
SRC := $(shell pwd)
KERNAL_SRC ?= /lib/modules/$(shell uname -r)
BUILD_DIR ?= $(KERNAL_SRC)/build
MODULE = samsung-galaxybook
VERSION = 0.1
DKMS_MODULE_DIR = /usr/src/$(MODULE)-$(VERSION)/

make:
	$(MAKE) -C $(BUILD_DIR) M=$(SRC) modules

modules_install:
	$(MAKE) -C $(KERNEL_SRC) M=$(SRC) modules_install

dkms_install:
	sudo mkdir -p $(DKMS_MODULE_DIR)

clean:
	rm -f $(SRC)/*.cmd && \
	rm -f $(SRC)/.*.cmd && \
	rm -f $(SRC)/*.ko && \
	rm -f $(SRC)/*.mod && \
	rm -f $(SRC)/*.mod.c && \
	rm -f $(SRC)/*.o && \
	rm -f $(SRC)/Module.symvers && \
	rm -f $(SRC)/modules.order
