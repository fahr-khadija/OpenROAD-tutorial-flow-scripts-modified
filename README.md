# OpenROAD-tutorial-flow-scripts-modified
# 7nm Physical Design Contest
## Project Scope

OpenROAD is a open-source RTL-to-GDSII  flow.  RecentlyThis tutorial also includes examples of useful design explorations and manual usage in key flow stages to help users gain a good understanding of the OpenROAD application flow, data organization, GUI and commands).  This paper discusses the suggested solution, which optimize the file  helpers.tcl  used in OpenRoad tutorial process


## Getting Started

## OpenROAD
 It is an integrated chip physical design tool that takes a design from from RTL to GDSII.It uses a hierarchical placement algorithm that aims to minimize wire length, and it provides several features to optimize timing and power consumption. OpenROAD is designed to be extensible and customizable, with a flexible architecture that allows users to add their own algorithms and features. 
 
## OpenROAD-flow-scripts(ORFS) 
This is a flow controller that provides a fully automated RTL-to-GDSII design flow .In ORFS, OpenROAD is used as a plug-in for the physical design stage, and it can be configured and customized to meet the specific needs of the design project.

## The OpenROAD-flow-scripts tutorial 
It is to run the complete OpenROAD based flow from RTL-to-GDS using OpenROAD Flow Scripts. This tutorial also includes examples of useful design explorations and manual usage in key flow stages to help users gain a good understanding of the OpenROAD application flow, data organization, GUI and commands


## The OpenROAD-flow-scripts optimize
In tutorial process ,there are few script as  drc_issue.tcl  example to trace a simple DRC violation and  drc_fix.tcl example Tcl script to clean and fix the DRC violation.

## I.	IMPROVEMENTS
There are some few suggestions for optimizing the code of helpers.tcl

*https://github.com/The-OpenROAD-Project/OpenROAD-flow-scripts/blob/master/flow/tutorials/scripts/drt/helpers.tcl*

***This modif avoids an error if the directory already exists

#### if { ![file exists $result_dir] } {

#### catch {file mkdir $result_dir} }


***The run  can be faster since it avoids the overhead of creating a new Tcl interpreter to execute the catch branch

***use file join instead of hard coding directory separators


#### set test_dir [file dirname [file normalize [info script]]]

#### set result_dir [file join $test_dir "results"]


***This ensures that directory separator for the operating system the script is running on 

Use exec file instead of open file for reading a file 

#### set stream [open $file r]
#### while { [gets $stream line] >= 0 } {
####   puts $line
#### }
#### close $stream

can be changed to 

#### puts [exec cat $file]
this can avoid  forking a new process to read the file 


***************
Use catch to handle errors when opening files

#### if { [catch {set stream1 [open $file1 r]}] } {
  error "Could not open file: $file1"
}
#### if { [catch {set stream2 [open $file2 r]}] } {
  error "Could not open file: $file2"
}

This ensures that errors when opening files are handled gracefully


              
                              REFERENCES
                              
       [1]	https://github.com/The-OpenROAD-Project/OpenROAD-flow-scripts 
       [2] https://github.com/yathAg/openroad_vsd_7nmContest#auto-tuner-installation
       [3]	https://github.com/The-OpenROAD-Project/OpenROAD-flow-scripts/blob/master/flow/tutorials/scripts/drt/drc_fix.tcl
       [4] https://vlsicad.ucsd.edu/Publications/Conferences/371/c371.pdf 
       [5] https://vlsicad.ucsd.edu/Publications/Conferences/370/c370.pdf

