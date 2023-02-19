---
layout: post
title: Programming OpenGL ES with ios
category: 编程开发
tags: game-engine
keywords: ios,OpenGL ES,pipeline
description: 
---
## Add the view controller's view to the window and display.
* Create a full-screen window.

        UIScreen *screen = [UIScreen mainScreen];
        CGRect bounds = [screen bounds];
        UIWindow *_window = [[UIWindow alloc] initWithFrame:bounds];
* Create class EAGLView inheriting UIView.

  * in header file
  
```
        @interface EAGLView : UIView{
        }
        - (id) initVithFrame:(CGRect)frame;
        /** creates an initializes an EAGLView with a frame, a color buffer format, a depth buffer format, a sharegroup, and multisamping */
        + (id) viewWithFrame:(CGRect)frame pixelFormat:(NSString*)format depthFormat:(GLuint)depth preserveBackbuffer:(BOOL)retained sharegroup:(EAGLSharegroup*)sharegroup multiSampling:(BOOL)multisampling numberOfSamples:(unsigned int)samples;
```
  * in text file
  
```
        - (id) initWithFrame:(CGRect)frame {
        	if (self = [super initWithFrame:frame]) {
            	
        	}
        }
        
        + (id) viewWithFrame:(CGRect)frame pixelFormat:(NSString*)format depthFormat:(GLuint)depth preserveBackbuffer:(BOOL)retained sharegroup:(EAGLSharegroup*)sharegroup multiSampling:(BOOL)multisampling numberOfSamples:(unsigned int)samples {
        	return [[[self alloc]initWithFrame:frame pixelFormat:format depthFormat:depth preserveBackbuffer:retained sharegroup:sharegroup multiSampling:multisampling numberOfSamples:samples] autorelease];
        }
        
```
    
* Initialize Frame.

        EAGLView *_glView = [EAGLView viewWithFrame: [window bounds]
                                     pixelFormat: kEAGLColorFormatRGBA8
                                     depthFormat: GL_DEPTH_COMPONENT16
                              preserveBackbuffer: NO
                                      sharegroup: nil
                                   multiSampling: NO
                                 numberOfSamples: 0 ];
* Use RootUIViewController, subclass of UIViewController, to manage EAGLView.

        RootUIViewController viewController = [[RootViewController alloc] initWithNibName:nil bundle:nil];
        viewController.wantsFullScreenLayout = YES;
        viewController.view = _glView;
* Add RootUIViewController to window.

        // Set RootViewController to window
        if ( [[UIDevice currentDevice].systemVersion floatValue] < 6.0) {
        	// AddSubView doesn't work on iOS6
        	[_window addSubview: viewController.view];
        } else {
        	// use this method on ios6
        	[_window setRootViewController:viewController];
        }
    
* Show the window.

        [_window makeKeyAndVisible];

# 
## Reference
