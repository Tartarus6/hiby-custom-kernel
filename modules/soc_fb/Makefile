# Out-of-tree build against the configured kernel tree:
#   make -C <kernel tree> M=$PWD ARCH=mips CROSS_COMPILE=mips-linux-gnu- modules
obj-m := soc_fb.o

# HIBY_MODEL=r1 builds it as the R1's firmware 2.0 module (HIBY_BOARD_R1);
# the sonix kernel defines HIBY_BOARD_<MODEL> for it from CONFIG_HIBY_MODEL.
ifneq ($(HIBY_MODEL),)
ccflags-y += -DHIBY_BOARD_$(shell echo '$(HIBY_MODEL)' | tr a-z A-Z)
endif

# The symbols of the HiBy modules it calls, so that modpost records them in
# "depends" as the vendor module does.
KBUILD_EXTRA_SYMBOLS := $(KBUILD_EXTMOD)/hiby.symvers
