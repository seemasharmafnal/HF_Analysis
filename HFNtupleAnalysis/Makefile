CXX     = g++
CXXFLAGS = -m64 -pipe -W -Wall -Woverloaded-virtual \
           -fsigned-char -fno-common -I$(ROOTSYS)/include
#           -fsigned-char -fno-common -stdlib=libc++ -I$(ROOTSYS)/include #worked on Mac
INCLUDE = $(shell root-config --cflags)
LIBS    = $(shell root-config --libs) 

LD            = g++
LDFLAGS       = -O2 -m64 

SOURCES = NtupleVariables.cc AnalyzeHFNtuples.cc 
HEADERS = NtupleVariables.h AnalyzeHFNtuples.h 
OBJECTS = $(SOURCES:.cc=.o)
#OBJS          = NtupleVariables.o AnalyzeHFNtuples.o 

EXECUTABLE = analyzeHFNtuples

all: $(SOURCES) $(EXECUTABLE)

$(EXECUTABLE): $(OBJECTS)
	@echo "Linking $(PROGRAM) ..."
	@echo "@$(CXX) $(LIBS) $(OBJECTS) -o $@"
	@$(CXX) $(LIBS) $(OBJECTS) -o $@
	@echo "done"

%.o: %.cc
	@echo Compiling $<...
	$(CXX) $(CXXFLAGS) -c -o $@ $< 


# Specifying the object files as intermediates deletes them automatically after the build process.
.INTERMEDIATE:  $(OBJECTS)

# The default target, which gives instructions, can be called regardless of whether or not files need to be updated.
.PHONY : clean
clean:
	rm -f $(OBJECTS) $(EXECUTABLE)

###
NtupleVariables.o: NtupleVariables.h
AnalyzeHFNtuples.o:NtupleVariables.h AnalyzeHFNtuples.h
