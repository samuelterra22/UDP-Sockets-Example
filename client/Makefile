############################# Makefile ##########################
# AUTHOR:   Samuel Terra Vieira                                 #
# ADDRESS:  Universidade Federal de Lavras                      #
# DATE:     23/09/2019                                          #
#################################################################

#################################################################
#                     Variable definition                       #
#################################################################

# The project name
PROJECT_NAME=client

# .c folder with files
C_SOURCE=$(wildcard ./source/*.c)

# .h folder with files
H_SOURCE=$(wildcard ./source/*.h)

# Object files
OBJ=$(subst .c,.o,$(subst source,objects,$(C_SOURCE)))

# Compiler and linker
CC=gcc

# Flags for compiler
CC_FLAGS=-c         \
         -W         \
         -Wall      \
#         -ansi      \
#         -pedantic

# Command used at clean target
RM = rm -rf

#################################################################
#                    Compilation and linking                    #
#################################################################

all: objFolder $(PROJECT_NAME)

$(PROJECT_NAME): $(OBJ)
	@ echo 'Building binary using GCC linker: $@'
	$(CC) $^ -o $@
	@ echo 'Finished building binary: $@'
	@ echo ' '

./objects/%.o: ./source/%.c ./source/%.h
	@ echo 'Building target using GCC compiler: $<'
	$(CC) $< $(CC_FLAGS) -o $@
	@ echo ' '

./objects/main.o: ./source/main.c $(H_SOURCE)
	@ echo 'Building target using GCC compiler: $<'
	$(CC) $< $(CC_FLAGS) -o $@
	@ echo ' '

objFolder:
	@ mkdir -p objects

clean:
	@ $(RM) ./objects/*.o $(PROJECT_NAME) *~
	@ rmdir objects

organize:
	@ mkdir -p source/
	@ [ -f *.c ] && mv *.c source/
	@ [ -f *.h ] && mv *.h source/
	@ echo 'Organized project. You can now compile it.'

run: $(PROJECT_NAME)
	./$(PROJECT_NAME)

.PHONY: all clean



