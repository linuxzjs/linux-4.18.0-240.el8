# SPDX-License-Identifier: GPL-2.0
# The loops are all 64-bit code
CFLAGS += -m64
CFLAGS += -I$(CURDIR)
CFLAGS += -D SELFTEST
CFLAGS += -maltivec

# Use our CFLAGS for the implicit .S rule & set the asm machine type
ASFLAGS = $(CFLAGS) -Wa,-mpower4

TEST_GEN_PROGS := copyuser_64 copyuser_power7 memcpy_64 memcpy_power7 memcpy_mcsafe_64
EXTRA_SOURCES := validate.c ../harness.c

top_srcdir = ../../../../..
include ../../lib.mk

$(OUTPUT)/copyuser_64:     CPPFLAGS += -D COPY_LOOP=test___copy_tofrom_user_base
$(OUTPUT)/copyuser_power7: CPPFLAGS += -D COPY_LOOP=test___copy_tofrom_user_power7
$(OUTPUT)/memcpy_64:       CPPFLAGS += -D COPY_LOOP=test_memcpy
$(OUTPUT)/memcpy_power7:   CPPFLAGS += -D COPY_LOOP=test_memcpy_power7
$(OUTPUT)/memcpy_mcsafe_64: memcpy_mcsafe_64.S $(EXTRA_SOURCES)
	$(CC) $(CPPFLAGS) $(CFLAGS) \
		-D COPY_LOOP=test_memcpy_mcsafe \
		-o $@ $^

$(TEST_GEN_PROGS): $(EXTRA_SOURCES)
