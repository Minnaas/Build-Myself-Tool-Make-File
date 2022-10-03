PROJDIR := $(realpath $(CURDIR)/..)
print-%:
	@echo $($(subst print-,,$@))


SOURCEDIR := $(PROJDIR)/Source

BUILDDIR := $(PROJDIR)/Build

TARGET = myApp.exe

VERBOSE = TRUE

DIRS = Folder0 Folder1 Folder2

SOURCEDIRS = $(foreach dir, $(DIRS), $(addprefix $(SOURCEDIR)/, $(dir)))
TARGETDIRS = $(foreach dir, $(DIRS), $(addprefix $(BUILDDIR)/, $(dir)))

INCLUDES = $(foreach dir, $(SOURCEDIRS), $(addprefix -I, $(dir)))

VPATH = $(SOURCEDIRS)

SOURCES = $(foreach dir,$(SOURCEDIRS),$(wildcard $(dir)/*.cpp))

OBJS := $(subst $(SOURCEDIR),$(BUILDDIR),$(SOURCES:.cpp=.o))

CC = g++

FILE = $(foreach dir,$(SOURCEDIRS),$(wildcard $(dir)/*.h)) #file.h

TEMP= $(notdir $(OBJS))
BUILD: $(TEMP)
	g++ $(OBJS) -o example.exe
	./example.exe
		@echo "----------BUILD Sucessfully------------"
vpath %.cpp $(SOURCES)
vpath %.o $(OBJS)
INC = da 
%.o:%.cpp $(FILE)
	g++ -c $< $(INCLUDES) -o $(foreach V, $(OBJS), $(if $(filter $@,$(notdir $(V))),$V))
#
clean: 
	-rm $(OBJS) 
	-rm example.exe
	@echo "----------Delete Sucessfully------------"