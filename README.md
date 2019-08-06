# rock_propagation

*This is code is the original work of Dom Brailsford, perhaps with help/advice from Robert Hatcher.*

Code to propagate GENIE reaction products in GEANT and then stuff them back into a GENIE record when they cross a particular boundary. This code is useful for simulating rock events in DUNE.

## Overview

Classes + executable project that propagates GHEP particles from a genie event record through a world geometry in geant4.  Particles which enter a volume with name 'volDetEnclosure'  or 'volDetector' have their state saved back into the genie GHEP event record and are recorded as a kIStStableFinalState.  The idea is that these GHEP event records could be passed to a different geant4 tracker downstream and these particles would have their tracking continue from the point that they entered the detector cavern.

## compiling

*Setup and building instructions are for Fermilab dunegpvm nodes*

The CMAKE project relies on GENIE and Geant4, as setup by the UPS system at FNAL.  The project does not use UPS directly for compilation but it does rely on a few UPS environment variables for genie,g4,libxml etc to be set so that CMAKE can find the relevant libararies/includes

To compile
1) Setup cmake, geant4 and genie ups products
2) $ source setup_rockprop.sh 
3) $ cd build
4) $ cmake ../
5) $ make
6) done!

To setup the compiled project after logging back in
1) Setup cmake, geant4 and genie ups products
2) $ source setup_rockprop.sh
3) done

## running

    $ runRockPropagation -f path/to/ghep_file.root -o output_name_prefix -g /path/to/geometry.gdml -s random_seed_number -n nevents_to_process

