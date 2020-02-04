.PHONY: all clean bin

CC 		   =	gcc
CXX 	   =	g++

CXXFLAGS   =	-std=c++11\
				-I../\
				-lz\
				-lpthread\

DEUBG_CXX  =	${CXXFLAGS} -g
RELEASE_CXX=	${CXXFLAGS}

source_cpp =	../common/files/file_reader.cpp \
		   		../common/files/file_writer.cpp \
		   		../common/files/gzstream.cpp \
				../common/log/log.cpp\
				../common/log/logfilter.cpp\
				../common/time/timetools.cpp\
				../common/string/stringtools.cpp\
				../common/args/argsparser.cpp\
				../biocommon/fasta/fasta.cpp\
				../biocommon/seq/seq.cpp\

source_o		= ${source_cpp:%.cpp=%.o}

.cpp.o:
	${CXX} ${DEUBG_CXX} -c $< -o $@

jobs = Split 

all :  ${jobs}




Split_cpp = Split.cpp
Split_o = Split.o
Split : clean ${Split_o} ${source_o} ../bin
	${CXX} ${Split_o} ${source_o} ${DEUBG_CXX} -o Split
	mv $@ ../bin/


jobs_o=  ${Split_o}

dirty	   =${jobs_o} ${jobs} ${source_o}

../bin:
	mkdir -p ../bin

clean:
	rm -rf ${dirty}

