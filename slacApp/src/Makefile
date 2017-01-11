TOP=../..

include $(TOP)/configure/CONFIG
#----------------------------------------
#  ADD MACRO DEFINITIONS AFTER THIS LINE
#========================================

# ================================================
# Build the IOC application
# ================================================
# This will attempt to build an IOC application 
# for every target including the host computer.
PROD_IOC = _APPNAME_

# Use the following for RTEMS Only IOCs
#PROD_IOC_RTEMS = _APPNAME_

# _APPNAME_.dbd will be created and installed
DBD += _APPNAME_.dbd

# _APPNAME_.dbd will be made up from these files:
_APPNAME__DBD += base.dbd
_APPNAME__DBD += devIocStats.dbd
_APPNAME__DBD += autosaveSupport.dbd
_APPNAME__DBD += caPutLog.dbd
_APPNAME__DBD += $(CEXP_DBDS)

# ================================================================================
# The system command will be mainly used by linux hosted IOCs
# Very useful for changing kernel thread priorities for kernel drivers
# ================================================================================
_APPNAME__DBD += system.dbd

# If you don't have an EVR comment the following two lines:
_APPNAME__DBD += evrSupport.dbd
_APPNAME__DBD += devMrfEr.dbd

# ======================================================================
# _APPNAME__registerRecordDeviceDriver.cpp derives from _APPNAME_.dbd
_APPNAME__SRCS += _APPNAME__registerRecordDeviceDriver.cpp

# Build the main IOC entry point where needed
_APPNAME__SRCS_DEFAULT += _APPNAME_Main.cpp
_APPNAME__SRCS_vxWorks += -nil-

# ========================================================================
# ========================================================================
# Add locally compiled object code
# For example, subroutines
# ========================================================================
# _APPNAME__SRCS += file1.c
# _APPNAME__SRCS += file2.c

# =====================================================
# Link in the code from other libraries
# =====================================================
# Needed to link in iocAdmin support
_APPNAME__LIBS += devIocStats

# Needed to link in autosave support
_APPNAME__LIBS += autosave

# Needed to link caPutLog support
_APPNAME__LIBS += caPutLog

# Needed to link cexpsh() support
_APPNAME__LIBS += $(CEXP_LIBS)


# =============================================
# Begin to link in the EVR support for
# RTEMS, linux, and linuxRT
# If you don't have an EVR, you can comment out 
# the lines below.
# =============================================
 _APPNAME__LIBS += evrSupport
 _APPNAME__LIBS += devMrfEr

ifneq ($(T_A),linuxRT-x86_64)
  ifneq ($(T_A),rhel6-x86_64)
       _APPNAME__LIBS += mrfVme64x
  endif
endif

ifeq ($(T_A),linuxRT-x86_64)
  _APPNAME__LIBS += drvMrf
endif

ifeq ($(T_A),rhel6-x86_64)
  _APPNAME__LIBS += drvMrf
endif
# =====================================================
# END EVR libraries
# =====================================================

# NOTE: To build SNL programs, SNCSEQ must be defined
# in the <top>/configure/RELEASE file

# To build SNL programs, SNCSEQ must be defined
# in the <top>/configure/RELEASE file
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


# Finally link IOC to the EPICS Base libraries
_APPNAME__LIBS += $(EPICS_BASE_IOC_LIBS)

#==============================================

include $(TOP)/configure/RULES
#----------------------------------------
#  ADD EXTRA GNUMAKE RULES BELOW HERE

