APPNAME = camcoeffs

include $(ISISROOT)/make/isismake.tsts

commands:
	$(APPNAME) IAKCODE=-41219 XCONSTCOEF=0.2589180702 \
		XSAMPLECOEF=-0.0069999992 XLINECOEF=0.0000033598 \
		YCONSTCOEF=-59.9867757282 YSAMPLECOEF=0.0000033598 \
		YLINECOEF=-0.0069999992 > $(OUTPUT)/naif.txt;
