include ../../Makefile.in

LIB = $(COMMON_LIB) $(SPHPK_LIB) $(FFTW_LIB) $(LAPACK95_LIB) $(PETSC_LIB) $(NETCDF_LIB) $(MKL_LIB) $(STATIC)
EXECUTABLES = tube initcond tube_init

all : $(EXECUTABLES)

lib : $(wildcard $(WORK_DIR)/common/*.F90)
	make -C $(WORK_DIR)/common

$(EXECUTABLES) : % : %.o $(wildcard $(COMMON_DIR)/*.F90)
	make lib
	$(FC) $(LDFLAGS) -o $@ $< $(LIB)

clean :
	-rm -f $(EXECUTABLES) *.o *.mod *.a core

# Dependency
.depend : $(wildcard *.F90)
	makedepf90 $^ > .depend

include .depend
# DO NOT DELETE
