APPNAME = jigsaw

include $(ISISROOT)/make/isismake.tsts

commands:
	
	$(LS) -1 $(INPUT)/*.cub > $(OUTPUT)/cube.lis;
	ulimit -n 100 && $(APPNAME) fromlist=$(OUTPUT)/cube.lis  \
		cnet=$(INPUT)/enc_global_fin.net \
		onet=$(OUTPUT)/largeDataset_out.net \
		update=no \
		radius=yes \
		point_radius_sigma=150 \
		errorpropagation=yes \
		camera_angles_sigma=2.0 \
		bundleout_txt=no \
		file_prefix=$(OUTPUT)/ > /dev/null;
	# The above command uses sed to do the following (in order):
	# 1. remove cube filename paths
	# 2. remove net filename paths
	# 3. remove digits beyond the fifth decimal place of decimal numbers
	# 4. remove date and time
	# 5. remove number of iterations
	$(CAT) $(OUTPUT)/residuals.csv \
		| perl -pe 's/(^|,|: )([^,:]+\/)([^,\/:]*\.)(net|cub)/\1\3\4/g' 2>/dev/null \
		> $(OUTPUT)/largeDataset_residuals.csv;
	$(CAT) $(OUTPUT)/bundleout_images.csv \
		| perl -pe 's/(^|,|: )([^,:]+\/)([^,\/:]*\.)(net|cub)/\1\3\4/g' 2>/dev/null \
		> $(OUTPUT)/largeDataset_bundleout_images.csv;
	$(RM) $(OUTPUT)/bundleout_images.csv > /dev/null;
	$(MV) $(OUTPUT)/bundleout_points.csv $(OUTPUT)/kargeDataset_bundleout_points.csv > /dev/null;
	$(RM)  print.prt > /dev/null;
	$(RM) $(OUTPUT)/residuals.csv > /dev/null;
	$(RM) $(OUTPUT)/cube.lis print.prt > /dev/null;
	> /dev/null;
