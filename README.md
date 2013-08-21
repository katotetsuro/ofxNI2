OSX:

Add to Run Script

	cp -R ../../../addons/ofxNI2/libs/OpenNI2/lib/osx/ "$TARGET_BUILD_DIR/$PRODUCT_NAME.app/Contents/MacOS/";
	cp -R ../../../addons/ofxNI2/libs/NiTE2/lib/osx/ "$TARGET_BUILD_DIR/$PRODUCT_NAME.app/Contents/MacOS/";
	
	
	
### OpenNI/NiTE 2.2.0
At OpenNI2.0.0 and NiTE2.0.0, user tracker sometimes (really rare case) crashes.(because of "exc arithmetic divide by zero")
So I update to 2.2.0.
But it hasn't test enough yet because it may take some days to reproduce that error. 

	
### If you want to update OpenNI/NiTE version
It won't work if you just copy the files..
#### change install name
libNiTE2.dylib
	
	install_name_tool -id @executable_path/libNiTE2.dylib /path/to/	libNiTE2.dylib
	install_name_tool -change libOpenNI2.dylib @executable_path/libOpenNI2.dylib /path/to/libNiTE2.dylib

OpenNI2.dylib

	install_name_tool -id @executable_path/libOpenNI2.dylib /path/to/libOpenNI2.dylib

libOniFile.dylib

	install_name_tool -id @executable_path/Drivers/libOniFile.dylib /path/to/libOniFile.dylib

libPS1080.dylib

	install_name_tool -id @executable_path/Drivers/libPS1080.dylib /path/to/libPS1080.dylib

In OpenNI.ini, change

	Repository=OpenNI2/Drivers
to

	Repository=Drivers