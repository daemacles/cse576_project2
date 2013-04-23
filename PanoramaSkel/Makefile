# Makefile for project 2

# Project 2 Files
PROJ2=Panorama
PROJ2_SRCS=BlendImages.cpp \
	   FeatureAlign.cpp \
	   FeatureSet.cpp \
	   WarpSpherical.cpp \
	   Project2.cpp
PROJ2_OBJS=$(patsubst %.cpp, %.o, $(PROJ2_SRCS))

# ImageLib files
IMAGELIB=ImageLib/libImageLib.a
IMAGELIB_SRCS=ImageLib/Convolve.cpp \
	      ImageLib/FileIO.cpp \
	      ImageLib/Image.cpp \
	      ImageLib/ImageProc.cpp \
              ImageLib/RefCntMem.cpp \
	      ImageLib/Transform.cpp
IMAGELIB_OBJS=$(patsubst %.cpp, %.o, $(IMAGELIB_SRCS))

ALL_OBJS=$(PROJ2_OBJS) $(IMAGELIB_OBJS)

PROJ2_DEPFILES=$(patsubst %.o, %.d, $(PROJ2_OBJS))
IMAGELIB_DEPFILES=$(patsubst %.o, %.d, $(IMAGELIB_OBJS))

NODEPS=clean

CXX=g++
CXXFLAGS=-g -Wall -Wno-sign-compare -O3
LIBS=-lfltk_images -lfltk -lpng -ljpeg -lX11 -lXext -lXi -lXmu
LIB_PATH=-LImageLib/

all: $(PROJ2)

-include $(PROJ2_OBJS:.o=.d)
-include $(IMAGELIB_OBJS:.o=.d)

%.o: %.cpp %.d
	$(CXX) $(CXXFLAGS) -o $@ -c $< -IImageLib -IFLTK

%.d: %.cpp
	$(CXX) $(CXXFLAGS) -IImageLib -MM -MT '$(patsubst %.cpp,%.o,$<)' $< -MF $@

$(IMAGELIB): $(IMAGELIB_OBJS) $(IMAGELIB_DEPFILES)
	ar r $(IMAGELIB) $(IMAGELIB_OBJS)

$(PROJ2): $(PROJ2_OBJS) $(PROJ2_DEPFILES) $(IMAGELIB)
	$(CXX) -o $@ $(PROJ2_OBJS) $(IMAGELIB) $(LIB_PATH) $(LIBS)

clean:
	rm -f $(ALL_OBJS) *~ $(PROJ2) $(PROJ2_DEPFILES) $(IMAGELIB_DEPFILES) $(IMAGELIB)

# Don't generate dependencies for all rules
ifeq (0, $(words $(findstring $(MAKECMDGOALS), $(NODEPS))))
	-include $(DEPFILES)
endif
