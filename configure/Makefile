TOP=..

include $(TOP)/configure/CONFIG

TARGETS = $(CONFIG_TARGETS)
CONFIGS += $(subst ../,,$(wildcard $(CONFIG_INSTALLS)))

CFG +=CONFIG_PROTO
CFG +=CONFIG_EDL

include $(TOP)/configure/RULES
