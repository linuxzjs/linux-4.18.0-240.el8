ccflags-y := -Idrivers/net/ethernet/chelsio/cxgb4

obj-$(CONFIG_CRYPTO_DEV_CHELSIO) += chcr.o
chcr-objs :=  chcr_core.o chcr_algo.o
#ifdef CONFIG_CHELSIO_TLS_DEVICE
chcr-objs += chcr_ktls.o
#endif
chcr-$(CONFIG_CHELSIO_IPSEC_INLINE) += chcr_ipsec.o
obj-$(CONFIG_CRYPTO_DEV_CHELSIO_TLS) += chtls/
