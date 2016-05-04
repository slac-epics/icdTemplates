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

#HV
DB += caenN1470.template
DB += caenN1470chan.template
DB += example_expanded.db

# Install Protocol File:
# Looks like we have a local copy
# Should come from a shared module, right?
# Ask Garth
DB_INSTALLS += $(TOP)/EtherCAT_TestApp/Db/caenN1470.proto

DB_INSTALLS +=$(MOTOR)/db/basic_asyn_motor.db

#HV
# Where is the Protocol file coming from so that it is shared??
#DB_INSTALLS += $(TOP)/caenN1470App/Db/caenN1470.proto
DB_INSTALLS += $(ASYN)/db/asynRecord.db

# =======================================================================
#----------------------------------------------------
# If <anyname>.db template is not named <anyname>*.template add
# <anyname>_TEMPLATE = <templatename>

include $(TOP)/configure/RULES
#----------------------------------------
#  ADD RULES AFTER THIS LINE

