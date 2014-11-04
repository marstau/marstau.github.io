---
layout: post
title: symbol not found for architecture armv7
category: 游戏技术
tags: error／unresolved
keywords: mac,ios,xcode,symbol
description: 
---
#Error
Undefined symbols for architecture armv7:

  "_curl_multi_perform", referenced from:

      NewWing::NWCurlMultiRunner::run(float) in NWHttpHelper.o

  "_curl_easy_getinfo", referenced from:

      NewWing::NWCurlMultiRunner::run(float) in NWHttpHelper.o

  "_curl_multi_remove_handle", referenced from:

      NewWing::NWCurlMultiRunner::~NWCurlMultiRunner() in NWHttpHelper.o

      NewWing::NWCurlMultiRunner::run(float) in NWHttpHelper.o

  "_curl_multi_add_handle", referenced from:

      NewWing::NWCurlMultiRunner::addHelper(NewWing::NWHttpHelper*, int) in NWHttpHelper.o

  "_curl_formadd", referenced from:

      NewWing::NWCurlMultiRunner::addHelper(NewWing::NWHttpHelper*, int) in NWHttpHelper.o

  "_curl_multi_info_read", referenced from:

      NewWing::NWCurlMultiRunner::run(float) in NWHttpHelper.o

  "_curl_easy_setopt", referenced from:

      NewWing::NWCurlMultiRunner::addHelper(NewWing::NWHttpHelper*, int) in NWHttpHelper.o

  "_curl_easy_perform", referenced from:

      NewWing::NWCurlMultiRunner::addHelper(NewWing::NWHttpHelper*, int) in NWHttpHelper.o

  "_curl_multi_cleanup", referenced from:

      NewWing::NWCurlMultiRunner::~NWCurlMultiRunner() in NWHttpHelper.o

  "_curl_easy_cleanup", referenced from:

      NewWing::NWCurlMultiRunner::addHelper(NewWing::NWHttpHelper*, int) in NWHttpHelper.o

      NewWing::NWCurlMultiRunner::~NWCurlMultiRunner() in NWHttpHelper.o

      NewWing::NWCurlMultiRunner::run(float) in NWHttpHelper.o

  "_curl_multi_fdset", referenced from:

      NewWing::NWCurlMultiRunner::run(float) in NWHttpHelper.o

  "_curl_global_cleanup", referenced from:

      NewWing::NWCurlMultiRunner::~NWCurlMultiRunner() in NWHttpHelper.o

  "_curl_global_init", referenced from:

      NewWing::NWCurlMultiRunner::sharedRunner() in NWHttpHelper.o

  "_curl_formfree", referenced from:

      NewWing::NWCurlMultiRunner::run(float) in NWHttpHelper.o

  "_curl_easy_init", referenced from:

      NewWing::NWCurlMultiRunner::addHelper(NewWing::NWHttpHelper*, int) in NWHttpHelper.o

  "_curl_multi_init", referenced from:

      NewWing::NWCurlMultiRunner::sharedRunner() in NWHttpHelper.o

ld: symbol(s) not found for architecture armv7

clang: error: linker command failed with exit code 1 (use -v to see invocation)



#Solution

不论如何设置architectures都没用,发现原来是.xcodeproj/project.pbxproj多了如下内容：

		4152071C19C05C0C00AE6735 /* AdsWrapper.mm in Sources */ = {isa = PBXBuildFile; fileRef = 415201F219C05C0B00AE6735 /* AdsWrapper.mm */; };
		4152071D19C05C0C00AE6735 /* IAPWrapper.mm in Sources */ = {isa = PBXBuildFile; fileRef = 415201F419C05C0B00AE6735 /* IAPWrapper.mm */; };
		4152071E19C05C0C00AE6735 /* PluginFactory.mm in Sources */ = {isa = PBXBuildFile; fileRef = 415201FB19C05C0B00AE6735 /* PluginFactory.mm */; };
		4152071F19C05C0C00AE6735 /* PluginProtocol.mm in Sources */ = {isa = PBXBuildFile; fileRef = 415201FD19C05C0B00AE6735 /* PluginProtocol.mm */; };
		4152072019C05C0C00AE6735 /* PluginUtilsIOS.mm in Sources */ = {isa = PBXBuildFile; fileRef = 415201FF19C05C0B00AE6735 /* PluginUtilsIOS.mm */; };
		4152072119C05C0C00AE6735 /* ProtocolAds.mm in Sources */ = {isa = PBXBuildFile; fileRef = 4152020019C05C0B00AE6735 /* ProtocolAds.mm */; };
		4152072219C05C0C00AE6735 /* ProtocolAnalytics.mm in Sources */ = {isa = PBXBuildFile; fileRef = 4152020119C05C0B00AE6735 /* ProtocolAnalytics.mm */; };
		4152072319C05C0C00AE6735 /* ProtocolIAP.mm in Sources */ = {isa = PBXBuildFile; fileRef = 4152020219C05C0B00AE6735 /* ProtocolIAP.mm */; };
		4152072419C05C0C00AE6735 /* ProtocolShare.mm in Sources */ = {isa = PBXBuildFile; fileRef = 4152020319C05C0B00AE6735 /* ProtocolShare.mm */; };
		4152072519C05C0C00AE6735 /* ProtocolSocial.mm in Sources */ = {isa = PBXBuildFile; fileRef = 4152020419C05C0B00AE6735 /* ProtocolSocial.mm */; };
		4152072619C05C0C00AE6735 /* ProtocolUser.mm in Sources */ = {isa = PBXBuildFile; fileRef = 4152020519C05C0B00AE6735 /* ProtocolUser.mm */; };
		4152072719C05C0C00AE6735 /* ShareWrapper.mm in Sources */ = {isa = PBXBuildFile; fileRef = 4152020719C05C0B00AE6735 /* ShareWrapper.mm */; };
		4152072819C05C0C00AE6735 /* SocialWrapper.mm in Sources */ = {isa = PBXBuildFile; fileRef = 4152020919C05C0B00AE6735 /* SocialWrapper.mm */; };
		4152072919C05C0C00AE6735 /* UserWrapper.mm in Sources */ = {isa = PBXBuildFile; fileRef = 4152020B19C05C0B00AE6735 /* UserWrapper.mm */; };
		4152072A19C05C0C00AE6735 /* PluginManager.cpp in Sources */ = {isa = PBXBuildFile; fileRef = 4152020C19C05C0B00AE6735 /* PluginManager.cpp */; };
		4152072B19C05C0C00AE6735 /* PluginParam.cpp in Sources */ = {isa = PBXBuildFile; fileRef = 4152020D19C05C0B00AE6735 /* PluginParam.cpp */; };




/* Begin PBXContainerItemProxy section */
		4152079819C05C0C00AE6735 /* PBXContainerItemProxy */ = {
			isa = PBXContainerItemProxy;
			containerPortal = 4152022A19C05C0B00AE6735 /* PluginProtocol.xcodeproj */;
			proxyType = 2;
			remoteGlobalIDString = FA09A321168ADBC2008C1C7B;
			remoteInfo = PluginProtocol;
		};
/* End PBXContainerItemProxy section */

/* Begin PBXFileReference section */
		415201D619C05C0B00AE6735 /* PluginFactory.h */ = {isa = PBXFileReference; fileEncoding = 4; lastKnownFileType = sourcecode.c.h; path = PluginFactory.h; sourceTree = "<group>"; };
		415201D719C05C0B00AE6735 /* PluginManager.h */ = {isa = PBXFileReference; fileEncoding = 4; lastKnownFileType = sourcecode.c.h; path = PluginManager.h; sourceTree = "<group>"; };
		415201D819C05C0B00AE6735 /* PluginParam.h */ = {isa = PBXFileReference; fileEncoding = 4; lastKnownFileType = sourcecode.c.h; path = PluginParam.h; sourceTree = "<group>"; };
		415201D919C05C0B00AE6735 /* PluginProtocol.h */ = {isa = PBXFileReference; fileEncoding = 4; lastKnownFileType = sourcecode.c.h; path = PluginProtocol.h; sourceTree = "<group>"; };
		415201DA19C05C0B00AE6735 /* ProtocolAds.h */ = {isa = PBXFileReference; fileEncoding = 4; lastKnownFileType = sourcecode.c.h; path = ProtocolAds.h; sourceTree = "<group>"; };
		415201DB19C05C0B00AE6735 /* ProtocolAnalytics.h */ = {isa = PBXFileReference; fileEncoding = 4; lastKnownFileType = sourcecode.c.h; path = ProtocolAnalytics.h; sourceTree = "<group>"; };
		415201DC19C05C0B00AE6735 /* ProtocolIAP.h */ = {isa = PBXFileReference; fileEncoding = 4; lastKnownFileType = sourcecode.c.h; path = ProtocolIAP.h; sourceTree = "<group>"; };
		415201DD19C05C0B00AE6735 /* ProtocolShare.h */ = {isa = PBXFileReference; fileEncoding = 4; lastKnownFileType = sourcecode.c.h; path = ProtocolShare.h; sourceTree = "<group>"; };
		415201DE19C05C0B00AE6735 /* ProtocolSocial.h */ = {isa = PBXFileReference; fileEncoding = 4; lastKnownFileType = sourcecode.c.h; path = ProtocolSocial.h; sourceTree = "<group>"; };
		415201DF19C05C0B00AE6735 /* ProtocolUser.h */ = {isa = PBXFileReference; fileEncoding = 4; lastKnownFileType = sourcecode.c.h; path = ProtocolUser.h; sourceTree = "<group>"; };
		415201F119C05C0B00AE6735 /* AdsWrapper.h */ = {isa = PBXFileReference; fileEncoding = 4; lastKnownFileType = sourcecode.c.h; path = AdsWrapper.h; sourceTree = "<group>"; };
		415201F219C05C0B00AE6735 /* AdsWrapper.mm */ = {isa = PBXFileReference; fileEncoding = 4; lastKnownFileType = sourcecode.cpp.objcpp; path = AdsWrapper.mm; sourceTree = "<group>"; };
		415201F319C05C0B00AE6735 /* IAPWrapper.h */ = {isa = PBXFileReference; fileEncoding = 4; lastKnownFileType = sourcecode.c.h; path = IAPWrapper.h; sourceTree = "<group>"; };
		415201F419C05C0B00AE6735 /* IAPWrapper.mm */ = {isa = PBXFileReference; fileEncoding = 4; lastKnownFileType = sourcecode.cpp.objcpp; path = IAPWrapper.mm; sourceTree = "<group>"; };
		415201F519C05C0B00AE6735 /* InterfaceAds.h */ = {isa = PBXFileReference; fileEncoding = 4; lastKnownFileType = sourcecode.c.h; path = InterfaceAds.h; sourceTree = "<group>"; };
		415201F619C05C0B00AE6735 /* InterfaceAnalytics.h */ = {isa = PBXFileReference; fileEncoding = 4; lastKnownFileType = sourcecode.c.h; path = InterfaceAnalytics.h; sourceTree = "<group>"; };
		415201F719C05C0B00AE6735 /* InterfaceIAP.h */ = {isa = PBXFileReference; fileEncoding = 4; lastKnownFileType = sourcecode.c.h; path = InterfaceIAP.h; sourceTree = "<group>"; };
		415201F819C05C0B00AE6735 /* InterfaceShare.h */ = {isa = PBXFileReference; fileEncoding = 4; lastKnownFileType = sourcecode.c.h; path = InterfaceShare.h; sourceTree = "<group>"; };
		415201F919C05C0B00AE6735 /* InterfaceSocial.h */ = {isa = PBXFileReference; fileEncoding = 4; lastKnownFileType = sourcecode.c.h; path = InterfaceSocial.h; sourceTree = "<group>"; };
		415201FA19C05C0B00AE6735 /* InterfaceUser.h */ = {isa = PBXFileReference; fileEncoding = 4; lastKnownFileType = sourcecode.c.h; path = InterfaceUser.h; sourceTree = "<group>"; };
		415201FB19C05C0B00AE6735 /* PluginFactory.mm */ = {isa = PBXFileReference; fileEncoding = 4; lastKnownFileType = sourcecode.cpp.objcpp; path = PluginFactory.mm; sourceTree = "<group>"; };
		415201FC19C05C0B00AE6735 /* PluginOCMacros.h */ = {isa = PBXFileReference; fileEncoding = 4; lastKnownFileType = sourcecode.c.h; path = PluginOCMacros.h; sourceTree = "<group>"; };
		415201FD19C05C0B00AE6735 /* PluginProtocol.mm */ = {isa = PBXFileReference; fileEncoding = 4; lastKnownFileType = sourcecode.cpp.objcpp; path = PluginProtocol.mm; sourceTree = "<group>"; };
		415201FE19C05C0B00AE6735 /* PluginUtilsIOS.h */ = {isa = PBXFileReference; fileEncoding = 4; lastKnownFileType = sourcecode.c.h; path = PluginUtilsIOS.h; sourceTree = "<group>"; };
		415201FF19C05C0B00AE6735 /* PluginUtilsIOS.mm */ = {isa = PBXFileReference; fileEncoding = 4; lastKnownFileType = sourcecode.cpp.objcpp; path = PluginUtilsIOS.mm; sourceTree = "<group>"; };
		4152020019C05C0B00AE6735 /* ProtocolAds.mm */ = {isa = PBXFileReference; fileEncoding = 4; lastKnownFileType = sourcecode.cpp.objcpp; path = ProtocolAds.mm; sourceTree = "<group>"; };
		4152020119C05C0B00AE6735 /* ProtocolAnalytics.mm */ = {isa = PBXFileReference; fileEncoding = 4; lastKnownFileType = sourcecode.cpp.objcpp; path = ProtocolAnalytics.mm; sourceTree = "<group>"; };
		4152020219C05C0B00AE6735 /* ProtocolIAP.mm */ = {isa = PBXFileReference; fileEncoding = 4; lastKnownFileType = sourcecode.cpp.objcpp; path = ProtocolIAP.mm; sourceTree = "<group>"; };
		4152020319C05C0B00AE6735 /* ProtocolShare.mm */ = {isa = PBXFileReference; fileEncoding = 4; lastKnownFileType = sourcecode.cpp.objcpp; path = ProtocolShare.mm; sourceTree = "<group>"; };
		4152020419C05C0B00AE6735 /* ProtocolSocial.mm */ = {isa = PBXFileReference; fileEncoding = 4; lastKnownFileType = sourcecode.cpp.objcpp; path = ProtocolSocial.mm; sourceTree = "<group>"; };
		4152020519C05C0B00AE6735 /* ProtocolUser.mm */ = {isa = PBXFileReference; fileEncoding = 4; lastKnownFileType = sourcecode.cpp.objcpp; path = ProtocolUser.mm; sourceTree = "<group>"; };
		4152020619C05C0B00AE6735 /* ShareWrapper.h */ = {isa = PBXFileReference; fileEncoding = 4; lastKnownFileType = sourcecode.c.h; path = ShareWrapper.h; sourceTree = "<group>"; };
		4152020719C05C0B00AE6735 /* ShareWrapper.mm */ = {isa = PBXFileReference; fileEncoding = 4; lastKnownFileType = sourcecode.cpp.objcpp; path = ShareWrapper.mm; sourceTree = "<group>"; };
		4152020819C05C0B00AE6735 /* SocialWrapper.h */ = {isa = PBXFileReference; fileEncoding = 4; lastKnownFileType = sourcecode.c.h; path = SocialWrapper.h; sourceTree = "<group>"; };
		4152020919C05C0B00AE6735 /* SocialWrapper.mm */ = {isa = PBXFileReference; fileEncoding = 4; lastKnownFileType = sourcecode.cpp.objcpp; path = SocialWrapper.mm; sourceTree = "<group>"; };
		4152020A19C05C0B00AE6735 /* UserWrapper.h */ = {isa = PBXFileReference; fileEncoding = 4; lastKnownFileType = sourcecode.c.h; path = UserWrapper.h; sourceTree = "<group>"; };
		4152020B19C05C0B00AE6735 /* UserWrapper.mm */ = {isa = PBXFileReference; fileEncoding = 4; lastKnownFileType = sourcecode.cpp.objcpp; path = UserWrapper.mm; sourceTree = "<group>"; };
		4152020C19C05C0B00AE6735 /* PluginManager.cpp */ = {isa = PBXFileReference; fileEncoding = 4; lastKnownFileType = sourcecode.cpp.cpp; path = PluginManager.cpp; sourceTree = "<group>"; };
		4152020D19C05C0B00AE6735 /* PluginParam.cpp */ = {isa = PBXFileReference; fileEncoding = 4; lastKnownFileType = sourcecode.cpp.cpp; path = PluginParam.cpp; sourceTree = "<group>"; };
		4152022919C05C0B00AE6735 /* PluginProtocol-Prefix.pch */ = {isa = PBXFileReference; fileEncoding = 4; lastKnownFileType = sourcecode.c.h; path = "PluginProtocol-Prefix.pch"; sourceTree = "<group>"; };
		4152022A19C05C0B00AE6735 /* PluginProtocol.xcodeproj */ = {isa = PBXFileReference; lastKnownFileType = "wrapper.pb-project"; path = PluginProtocol.xcodeproj; sourceTree = "<group>"; };


		415201D419C05C0B00AE6735 /* protocols */ = {
			isa = PBXGroup;
			children = (
				415201D519C05C0B00AE6735 /* include */,
				415201E019C05C0B00AE6735 /* platform */,
				4152020C19C05C0B00AE6735 /* PluginManager.cpp */,
				4152020D19C05C0B00AE6735 /* PluginParam.cpp */,
				4152022819C05C0B00AE6735 /* proj.ios */,
			);
			path = protocols;
			sourceTree = "<group>";
		};
		415201D519C05C0B00AE6735 /* include */ = {
			isa = PBXGroup;
			children = (
				415201D619C05C0B00AE6735 /* PluginFactory.h */,
				415201D719C05C0B00AE6735 /* PluginManager.h */,
				415201D819C05C0B00AE6735 /* PluginParam.h */,
				415201D919C05C0B00AE6735 /* PluginProtocol.h */,
				415201DA19C05C0B00AE6735 /* ProtocolAds.h */,
				415201DB19C05C0B00AE6735 /* ProtocolAnalytics.h */,
				415201DC19C05C0B00AE6735 /* ProtocolIAP.h */,
				415201DD19C05C0B00AE6735 /* ProtocolShare.h */,
				415201DE19C05C0B00AE6735 /* ProtocolSocial.h */,
				415201DF19C05C0B00AE6735 /* ProtocolUser.h */,
			);
			path = include;
			sourceTree = "<group>";
		};
		415201E019C05C0B00AE6735 /* platform */ = {
			isa = PBXGroup;
			children = (
				415201F019C05C0B00AE6735 /* ios */,
			);
			path = platform;
			sourceTree = "<group>";
		};
		415201F019C05C0B00AE6735 /* ios */ = {
			isa = PBXGroup;
			children = (
				415201F119C05C0B00AE6735 /* AdsWrapper.h */,
				415201F219C05C0B00AE6735 /* AdsWrapper.mm */,
				415201F319C05C0B00AE6735 /* IAPWrapper.h */,
				415201F419C05C0B00AE6735 /* IAPWrapper.mm */,
				415201F519C05C0B00AE6735 /* InterfaceAds.h */,
				415201F619C05C0B00AE6735 /* InterfaceAnalytics.h */,
				415201F719C05C0B00AE6735 /* InterfaceIAP.h */,
				415201F819C05C0B00AE6735 /* InterfaceShare.h */,
				415201F919C05C0B00AE6735 /* InterfaceSocial.h */,
				415201FA19C05C0B00AE6735 /* InterfaceUser.h */,
				415201FB19C05C0B00AE6735 /* PluginFactory.mm */,
				415201FC19C05C0B00AE6735 /* PluginOCMacros.h */,
				415201FD19C05C0B00AE6735 /* PluginProtocol.mm */,
				415201FE19C05C0B00AE6735 /* PluginUtilsIOS.h */,
				415201FF19C05C0B00AE6735 /* PluginUtilsIOS.mm */,
				4152020019C05C0B00AE6735 /* ProtocolAds.mm */,
				4152020119C05C0B00AE6735 /* ProtocolAnalytics.mm */,
				4152020219C05C0B00AE6735 /* ProtocolIAP.mm */,
				4152020319C05C0B00AE6735 /* ProtocolShare.mm */,
				4152020419C05C0B00AE6735 /* ProtocolSocial.mm */,
				4152020519C05C0B00AE6735 /* ProtocolUser.mm */,
				4152020619C05C0B00AE6735 /* ShareWrapper.h */,
				4152020719C05C0B00AE6735 /* ShareWrapper.mm */,
				4152020819C05C0B00AE6735 /* SocialWrapper.h */,
				4152020919C05C0B00AE6735 /* SocialWrapper.mm */,
				4152020A19C05C0B00AE6735 /* UserWrapper.h */,
				4152020B19C05C0B00AE6735 /* UserWrapper.mm */,
			);
			path = ios;
			sourceTree = "<group>";
		};
		4152022819C05C0B00AE6735 /* proj.ios */ = {
			isa = PBXGroup;
			children = (
				4152022919C05C0B00AE6735 /* PluginProtocol-Prefix.pch */,
				4152022A19C05C0B00AE6735 /* PluginProtocol.xcodeproj */,
			);
			path = proj.ios;
			sourceTree = "<group>";
		};
		4152022B19C05C0B00AE6735 /* Products */ = {
			isa = PBXGroup;
			children = (
				4152079919C05C0C00AE6735 /* libPluginProtocol.a */,
			);
			name = Products;
			sourceTree = "<group>";
		};
		4152FCAF19C05C0800AE6735 /* plugin */ = {
			isa = PBXGroup;
			children = (
				4152FCC919C05C0800AE6735 /* plugins */,
				415201D419C05C0B00AE6735 /* protocols */,
			);
			name = plugin;
			path = libs/plugin;
			sourceTree = "<group>";
		};
		4152FCC919C05C0800AE6735 /* plugins */ = {
			isa = PBXGroup;
			children = (
			);
			path = plugins;
			sourceTree = "<group>";
		};
		
		
		
		
		
				4152FCAF19C05C0800AE6735 /* plugin */,
				
				
							projectReferences = (
				{
					ProductGroup = 4152022B19C05C0B00AE6735 /* Products */;
					ProjectRef = 4152022A19C05C0B00AE6735 /* PluginProtocol.xcodeproj */;
				},
			);
			
			
			/* Begin PBXReferenceProxy section */
		4152079919C05C0C00AE6735 /* libPluginProtocol.a */ = {
			isa = PBXReferenceProxy;
			fileType = archive.ar;
			path = libPluginProtocol.a;
			remoteRef = 4152079819C05C0C00AE6735 /* PBXContainerItemProxy */;
			sourceTree = BUILT_PRODUCTS_DIR;
		};
/* End PBXReferenceProxy section */



				4152072319C05C0C00AE6735 /* ProtocolIAP.mm in Sources */,
				
				
									"$(PROJECT_DIR)/ydsg/libs/plugin/plugins/admob/proj.ios/Admob",
					"$(PROJECT_DIR)/ydsg/libs/plugin/plugins/flurry/proj.ios/FlurryAds",
					"$(PROJECT_DIR)/ydsg/libs/plugin/plugins/flurry/proj.ios",
					"$(PROJECT_DIR)/ydsg/libs/plugin/plugins/umeng/proj.ios",