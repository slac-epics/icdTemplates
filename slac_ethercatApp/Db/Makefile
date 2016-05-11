TOP=../..
include $(TOP)/configure/CONFIG
#----------------------------------------
#  ADD MACRO DEFINITIONS AFTER THIS LINE

#----------------------------------------------------
#  Optimization of db files using dbst (DEFAULT: NO)
#DB_OPT = YES

#----------------------------------------------------
# Create and install (or just install)
# databases, templates, substitutions like this
DB += EK1101.template
DB += CX5020.template
DB += EL7041.template
DB += EL70xx.template
DB += EL3702.template
DB += EL5001.template
DB += E1250-EC-UC.template

# BSA Test
DB += bsaSimulator.db

# ====================================================
# CAEN HV Bias: Model 1470
# ====================================================
DB_INSTALLS += $(CAENN1470)/db/caenN1470.template
DB_INSTALLS += $(CAENN1470)/db/caenN1470chan.template
DB_INSTALLS += $(CAENN1470)/db/example_expanded.db

# Install Protocol File:
DB_INSTALLS += $(CAENN1470)/db/caenN1470.proto
# ====================================================

DB_INSTALLS +=$(MOTOR)/db/basic_asyn_motor.db

DB_INSTALLS += $(ASYN)/db/asynRecord.db
DB_INSTALLS += $(COUNTER)/db/APCI1710Counter.db

# ========================================
# Install timing/event related databases  
# ========================================
DB_INSTALLS += $(EVENT)/db/EvrPmc.db
DB_INSTALLS += $(EVENT)/db/EvrPci.db
DB_INSTALLS += $(EVENT)/db/Pattern.db
DB_INSTALLS += $(EVENT)/db/PCI-trig.db
DB_INSTALLS += $(EVENT)/db/PMC-trig.db
DB_INSTALLS += $(EVENT)/db/Bsa.db

# ========================================
# Install Common databases needed by All IOCs
# ===============================================================================
# Install databases from iocAdmin package
# These databases support IOC Health and Monitoring
# ===============================================================================
# SoftIOC
DB_INSTALLS += $(IOCADMIN)/db/iocAdminSoft.db
#
DB_INSTALLS += $(IOCADMIN)/db/iocAdminScanMon.db
DB_INSTALLS += $(IOCADMIN)/db/iocScanMonSum.db
DB_INSTALLS += $(IOCADMIN)/db/iocScanMon.db
IOCRELEASE_DB += iocRelease.db
# ===============================================================================

# ===============================================================================
# Install Database to support reading the status of the autosave package
# =============================================================================
DB_INSTALLS += $(AUTOSAVE)/db/save_restoreStatus.db
# ===============================================================================


# =======================================================================
#----------------------------------------------------
# If <anyname>.db template is not named <anyname>*.template add
# <anyname>_TEMPLATE = <templatename>

include $(TOP)/configure/RULES
#----------------------------------------
#  ADD RULES AFTER THIS LINE

