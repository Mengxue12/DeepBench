all: gemm conv sparse

BIN_DIR?=bin
EIGEN_PATH?=/usr/local/eigen
MKDIR=mkdir -p
ARM_COMPUTE_INCLUDE_PATH?=/usr/local/ARMComputeLib
ARM_COMPUTE_LIB_PATH?=$(ARM_COMPUTE_INCLUDE_PATH)/build
KERNELS_DIR=../kernels/

gemm: gemm_bench.cc
	$(MKDIR) $(BIN_DIR)
	g++ -O3 --std=c++11 -I $(KERNELS_DIR) -lpthread -o bin/gemm_bench $<

sparse: sparse_bench.cpp
	$(MKDIR) $(BIN_DIR)
	g++ -O3 -std=c++11  -o bin/sparse_bench $< \
		-I $(EIGEN_PATH) -I $(KERNELS_DIR)

conv: convolution.cpp
	$(MKDIR) $(BIN_DIR)
	g++ -O3 -std=c++14 -I $(ARM_COMPUTE_INCLUDE_PATH) -I $(ARM_COMPUTE_INCLUDE_PATH)/include -I $(KERNELS_DIR) $< -o bin/conv_bench -L $(ARM_COMPUTE_LIB_PATH) -larm_compute -Wl,-rpath,$(shell realpath $(ARM_COMPUTE_LIB_PATH))

clean:
	rm -rf $(BIN_DIR)
