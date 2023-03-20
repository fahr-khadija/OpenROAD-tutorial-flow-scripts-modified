# OpenROAD-tutorial-flow-scripts-modified
## Project Scope

OpenROAD is a open-source RTL-to-GDSII  flow.  RecentlyThis tutorial also includes examples of useful design explorations and manual usage in key flow stages to help users gain a good understanding of the OpenROAD application flow, data organization, GUI and commands).  This paper discusses the suggested solution, which optimize the file  helpers.tcl  used in OpenRoad tutorial process


## Getting Started

## OpenROAD
 It is an integrated chip physical design tool that takes a design from from RTL to GDSII.It uses a hierarchical placement algorithm that aims to minimize wire length, and it provides several features to optimize timing and power consumption. OpenROAD is designed to be extensible and customizable, with a flexible architecture that allows users to add their own algorithms and features. 
 
## OpenROAD-flow-scripts(ORFS) 
This is a flow controller that provides a fully automated RTL-to-GDSII design flow .In ORFS, OpenROAD is used as a plug-in for the physical design stage, and it can be configured and customized to meet the specific needs of the design project.

## The OpenROAD-flow-scripts tutorial is to run the complete OpenROAD based flow from RTL-to-GDS using OpenROAD Flow Scripts. This tutorial also includes examples of useful design explorations and manual usage in key flow stages to help users gain a good understanding of the OpenROAD application flow, data organization, GUI and commands
In tutorial process ,there are few script as  drc_issue.tcl  example to trace a simple DRC violation and  drc_fix.tcl example Tcl script to clean and fix the DRC violation.

