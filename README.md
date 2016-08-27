# gles2-bc-nacl

Initial code migrated from Google Code Archive at: https://code.google.com/archive/p/gles2-bc/

Web site: http://johannesvuorinen.com/portfolio-item/opengl-es-2-0-backward-compatible/

This branch was originally imported and maintained by Collin Jackson. It was then updated to work as
a iOS Framework on modern XCode, and yes, I removed samples, moved folders, migrated things, removed stubs,
removed folders that were useless for the creation of a simple framework. So this is a really stripped down
version. Files that weren't updated were deleted (Sorry, Makefile).


## From the Google Code Archive:

gles2-bc is an open source C++ library which makes the non-backward compatible OpenGL ES 2.0 API backward compatible to ease the development with various OpenGL ES APIs. The project started as a Master's Thesis project, and has then continued as an open source project. The Master's Thesis is available online in PDF format. It gives a thorough explanation of the implementation, the motivation behind it, and shows the test results.

You are free to use and modify the implementation. Please report if you find any bugs or have improvement ideas. You are also more than welcome to participate in the project. It is not mandatory to inform me if you use the implementation in some project, but I would certainly like if you do so.

### Motivation

For example, the iPhone OS platform supports OpenGL ES 1.1 and OpenGL ES 2.0. The iPhones and iPod touches before iPhone 3GS support only OpenGL ES 1.1, while the iPhone 3GS also supports OpenGL ES 2.0. Currently most applications are developed using the OpenGL ES 1.1 API because the majority of the iPhone/iPod touch users own an OpenGL ES 1.1 supporting device. It would be non-cost-efficient to develop a separate code path for OpenGL ES 2.0. The point of this project is to enable developers to use the OpenGL ES 1.1 API code, and add the OpenGL ES 2.0 API code to it for special effects or other stuff which are efficiently possible only with OpenGL ES 2.0. Thus, the idea is the same as with desktop OpenGL 2.0 API which is backward compatible.

In addition, the implementation includes a few features which are added API functionality to provide ease use of advanced features without knowing anything about OpenGL ES 2.0 and shaders. Currently there are two features implemented: per-fragment lighting and texture blur.

### Implementation

The implementation is written with C++, and includes only a few lines of Objective-C code because of the iPhone OS platform. However, one goal of the project is to port the implementation to other platforms supporting OpenGL ES 2.0 when they are available. The implementation is flexible allowing the developer to control the amount of generated shaders.

### Testing

The implementation has been tested with a test application. Read more about it from the Master's Thesis. The OpenGL ES Conformance tests have not been run. There are currently no known projects which use the implementation.

### Additional API functionality
- glHint(GL_LIGHTING_HINT, GL_NICEST)
- uses per-fragment lighting if using an OpenGL ES 2.0 context
- glTexEnvi(GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, GL_BLUR)
- glTexEnvf(GL_TEXTURE_ENV, GL_BLUR_AMOUNT, 0.01f)
- enables texture blur with amount 0.01f
- used for example to create a post-processing blur effect

### Known limitations
- currently supports only iPhone platform
- porting to some other platforms should be easy
- flat shading is not supported (glShadeModel(GL_FLAT))
- fixed-point versions of the OpenGL ES 1.x API functions are not supported
- glLogicOp is not supported
- glColor4* is not supported
- glMultiTexCoord4* is not supported
- glNormal3* is not supported
- glPointSize is not supported
- various glGet* functions are not supported
- glColorPointer supports only GL_FLOAT type
- Maximum of 3 simultaneous texture units are supported
- Maximum of 3 simultaneous lights are supported

### Future plans
- optimize
- read configuration variables and state and non-state uniforms and attributes from config files
- fix the known limitations
- offline preprocessing
- dynamic shader generation approach in addition to the preprocessor approach
