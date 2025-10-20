timestamp = $(shell date "+%Y.%m.%d-%H.%M.%S")
define build =
helm dependency update
helm package . -d helm
endef

SUBDIRS := $(wildcard components/*/.)
CURRENT_DIR := $(notdir $(shell pwd))

.PHONY: all build $(SUBDIRS) install test uninstall clean
all: build install test uninstall clean

build: $(SUBDIRS) helm/*.tgz
helm/*.tgz:
	$(build)

$(SUBDIRS):
	$(MAKE) -C $@ $(MAKECMDGOALS)


install:
	helm install $(CURRENT_DIR) helm/*.tgz

uninstall:
	docker delete pod playwright 2> /dev/null || true
	helm uninstall $(CURRENT_DIR) 2> /dev/null || true

clean: $(SUBDIRS)
	rm -rf charts helm