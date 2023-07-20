# Define the Haskell compiler and compiler flags
GHC = ghc
GHC_FLAGS = -O2

# Define the build directory
BUILD_DIR = build

# Define the source files and object files
SRC_FILES = $(wildcard *.hs)
OBJ_FILES = $(patsubst %.hs, $(BUILD_DIR)/%.o, $(SRC_FILES))

# Get the base name of the first Haskell source file (without the .hs extension)
EXECUTABLE := $(basename $(notdir $(firstword $(SRC_FILES))))

# Default target: build the executable
all: $(BUILD_DIR) $(BUILD_DIR)/$(EXECUTABLE)

# Rule to create the build directory
$(BUILD_DIR):
	mkdir -p $(BUILD_DIR)

# Rule to build the executable
$(BUILD_DIR)/$(EXECUTABLE): $(OBJ_FILES)
	$(GHC) $(GHC_FLAGS) -o $@ $^

# Rule to build object files from Haskell source files
$(BUILD_DIR)/%.o: %.hs
	$(GHC) $(GHC_FLAGS) -c $< -o $@

# Clean target: remove the build directory
clean:
	rm -rf $(BUILD_DIR)

# Run target: build and run the executable
run: $(BUILD_DIR)/$(EXECUTABLE)
	./$(BUILD_DIR)/$(EXECUTABLE)
