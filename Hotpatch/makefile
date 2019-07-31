# makefile

#
# Patches/Installs/Builds DSDT patches for Lenovo u430
#
# Created by RehabMan 
#

# set build products
BUILDDIR=./build
PRODUCTS=$(BUILDDIR)/SSDT-HACK.aml  $(BUILDDIR)/SSDT-PNLF-GFX0.aml $(BUILDDIR)/SSDT-PNLF.aml

IASLFLAGS=-vw 2095 -vw 2146
IASL=./iasl

.PHONY: all
all: $(PRODUCTS)

$(BUILDDIR)/%.aml: %.dsl
	$(IASL) $(IASLFLAGS) -p $@ $<

.PHONY: clean
clean:
	rm -f $(BUILDDIR)/*.dsl $(BUILDDIR)/*.aml

.PHONY: install
install: $(AML_PRODUCTS)
	$(eval EFIDIR:=$(shell ./mount_efi.sh))
	rm -f "$(EFIDIR)"/EFI/CLOVER/ACPI/patched/DSDT.aml
	rm -f "$(EFIDIR)"/EFI/CLOVER/ACPI/patched/SSDT-*.aml "$(EFIDIR)"/EFI/CLOVER/ACPI/patched/SSDT.aml
	cp $(AML_PRODUCTS) "$(EFIDIR)"/EFI/CLOVER/ACPI/patched

