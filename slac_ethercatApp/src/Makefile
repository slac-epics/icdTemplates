TOP=../..

include $(TOP)/configure/CONFIG
#----------------------------------------
#  ADD MACRO DEFINITIONS AFTER THIS LINE
#========================================
# =====================================================
# Path to "NON EPICS" External PACKAGES: USER INCLUDES
#======================================================
USR_INCLUDES += $(ZLIB_INCLUDE)
USR_INCLUDES += $(XZ_INCLUDE)
USR_INCLUDES += $(LIBXML2_INCLUDE)
USR_INCLUDES += $(PCRE_INCLUDE)
# =====================================================

#======================================================
# PATH TO "NON EPICS" EXTERNAL PACKAGES: USER LIBRARIES
#======================================================
z_DIR = $(ZLIB_LIB)
lzma_DIR = $(XZ_LIB)
xml2_DIR = $(LIBXML2_LIB)
pcre_DIR = $(PCRE_LIB)
# =====================================================

# ======================================================
# LINK "NON EPICS" EXTERNAL PACKAGE LIBRARIES STATICALLY
#=======================================================
USR_LIBS_Linux += xml2 z lzma pcre
# ======================================================


# ================================================
# Build the IOC application
# ================================================
# This will attempt to build an IOC application 
# for every target including the host computer.
# ================================================

PROD_IOC_Linux += _APPNAME_

_APPNAME__INCLUDES += $(ECASYN)/include

# _APPNAME_.dbd will be created and installed
DBD += _APPNAME_.dbd

# _APPNAME_.dbd will be made up from these files:
_APPNAME__DBD += base.dbd
_APPNAME__DBD += asyn.dbd
_APPNAME__DBD += asynRecord.dbd
_APPNAME__DBD += drvAsynSerialPort.dbd
_APPNAME__DBD += drvAsynIPPort.dbd
_APPNAME__DBD += stream.dbd 
_APPNAME__DBD += ecAsyn.dbd
_APPNAME__DBD += motorRecord.dbd
_APPNAME__DBD += motorSupport.dbd
_APPNAME__DBD += EtherCATMotorSupport.dbd
_APPNAME__DBD += LinmotMotorSupport.dbd

_APPNAME__DBD += apci1710.dbd
_APPNAME__DBD += apci1710Support.dbd

_APPNAME__DBD += devIocStats.dbd
_APPNAME__DBD += autosaveSupport.dbd
_APPNAME__DBD += caPutLog.dbd

_APPNAME__DBD += drvUioPciGen.dbd
_APPNAME__DBD += devBusMapped.dbd
_APPNAME__DBD += epicspci.dbd
_APPNAME__DBD += $(CEXP_DBDS)

# The system command is available for all architectures
_APPNAME__DBD += system.dbd

# If you have an EVR uncomment the following two lines:
 _APPNAME__DBD += evrSupport.dbd
 _APPNAME__DBD += devMrfEr.dbd

# performance measurment module
 _APPNAME__DBD += drvPerfMeasure.dbd
# =========================================================

# ======================================================================
# <name>_registerRecordDeviceDriver.cpp will be created from <name>.dbd
_APPNAME__SRCS += _APPNAME__registerRecordDeviceDriver.cpp
_APPNAME__SRCS_DEFAULT += _APPNAME_Main.cpp
_APPNAME__SRCS_vxWorks += -nil-


_APPNAME__LIBS += ecAsyn 
_APPNAME__LIBS += motor
_APPNAME__LIBS += EtherCATMotor
_APPNAME__LIBS += LinmotMotor
_APPNAME__LIBS += asyn
_APPNAME__LIBS += stream
_APPNAME__LIBS += rtutils scannerlib
_APPNAME__LIBS += apci1710 

_APPNAME__INCLUDES += $(ECASYN)/include

# =====================================================
# Link in the code from other libraries
# =====================================================
# Needed to link in iocAdmin support
_APPNAME__LIBS += devIocStats

# Needed to link in autosave support
_APPNAME__LIBS += autosave

# Needed to link caPutLog support
_APPNAME__LIBS += caPutLog

# ===================================
# Needed to link in the EVR support
# ===================================
_APPNAME__LIBS += evrSupport
_APPNAME__LIBS += devMrfEr


ifeq ($(T_A),linuxRT-x86_64)
   _APPNAME__LIBS += drvMrf
     evrma_DIR = $(EVRMA_LIB)
       _APPNAME__LIBS += evrma
endif

ifeq ($(T_A),rhel6-x86_64)
  _APPNAME__LIBS += drvMrf
  evrma_DIR = $(EVRMA_LIB)
  _APPNAME__LIBS += evrma
endif

_APPNAME__LIBS += drvUioPciGen
_APPNAME__LIBS += devBusMapped
_APPNAME__LIBS += epicspci

_APPNAME__LIBS += perfMeasure

_APPNAME__LIBS += $(CEXP_LIBS)

# =======================================================
# NOTE: To build SNL programs, SNCSEQ must be defined
# in the <top>/configure/RELEASE file
# =======================================================
ifneq ($(SNCSEQ),)
     # Build sncExample into _APPNAME_Support
    sncExample_SNCFLAGS += +r
    _APPNAME__DBD += sncExample.dbd
    # A .stt sequence program is *not* pre-processed:
    _APPNAME_Support_SRCS += sncExample.stt
    _APPNAME_Support_LIBS += seq pv
    _APPNAME__LIBS += seq pv

    # Build sncProgram as a standalone program
    PROD_HOST += sncProgram
    sncProgram_SNCFLAGS += +m
    # A .st sequence program *is* pre-processed:
    sncProgram_SRCS += sncProgram.st
    sncProgram_LIBS += seq pv
    sncProgram_LIBS += $(EPICS_BASE_HOST_LIBS)
endif
# =========================================================

# Finally link IOC to the EPICS Base libraries
_APPNAME__LIBS += $(EPICS_BASE_IOC_LIBS)


# ==================================================
# Install external epics executable
# Install scanner program from Ethercat epics module
#===================================================
BIN_INSTALLS += $(ECASYN_BIN)/scanner

#===================================================

include $(TOP)/configure/RULES
#----------------------------------------
#  ADD RULES AFTER THIS LINE

