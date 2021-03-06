bogart
~~~~~~

::

  usage: bogart -o outputName -O ovlStore -G gkpStore -T tigStore
  
    -O         Mandatory path to an ovlStore.
    -G         Mandatory path to a gkpStore.
    -T         Mandatory path to a tigStore (can exist or not).
    -o prefix  Mandatory name for the output files
  
    -B b       Target number of fragments per tigStore (consensus) partition
  
  Algorithm Options
  
    -gs        Genome size in bases.
  
    -RS        Remove edges to spur reads from best overlap graph.
    -NS        Don't seed promiscuous unitigs with suspicious reads.
    -CS        Don't place contained reads in singleton unitigs.
    -RW t      Remove weak overlaps, those in the lower t fraction of erates per overlap end.
    -J         Join promiscuous unitigs using unused best edges.
    -SR        Shatter repeats, don't rebuild.
    -R         Shatter repeats (-SR), then rebuild them
    -RL len    Force reads below 'len' bases to be singletons.
                 This WILL cause CGW to fail; diagnostic only.
  
    -threads N Use N compute threads during repeat detection.
                 0 - use OpenMP default (default)
                 1 - use one thread
  
  Overlap Selection - an overlap will be considered for use in a unitig under
                      the following conditions:
  
    When constructing the Best Overlap Graph and Promiscuous Unitigs ('g'raph):
      -eg 0.020   no more than 0.020 fraction (2.0%) error
  
    When popping bubbles ('b'ubbles):
      -eb 0.045   no more than 0.045 fraction (4.5%) error when bubble popping
  
    When merging unitig ends ('m'erging):
      -em 0.045   no more than 0.045 fraction (4.5%) error when merging unitig ends
  
    When detecting repeats ('r'epeats):
      -er 0.045   no more than 0.045 fraction (4.5%) error when detecting repeats
  
    When loading overlaps, an inflated maximum (to allow reruns with different error rates):
      -eM 0.05   no more than 0.05 fraction (5.0%) error in any overlap loaded into bogart
                 the maximum used will ALWAYS be at leeast the maximum of the four error rates
  
    For all, the lower limit on overlap length
      -el 40      no shorter than 40 bases
  
  Overlap Storage
  
      -M gb    Use at most 'gb' gigabytes of memory for storing overlaps.
      -N num   Load at most 'num' overlaps per read.
  
      -create  Only create the overlap graph, save to disk and quit.
      -save    Save the overlap graph to disk, and continue.
  
  Debugging and Logging
  
    -D <name>  enable logging/debugging for a specific component.
    -d <name>  disable logging/debugging for a specific component.
                 overlapQuality
                 overlapsUsed
                 chunkGraph
                 intersections
                 populate
                 intersectionBreaking
                 intersectionBubbles
                 intersectionBubblesDebug
                 intersectionJoining
                 intersectionJoiningDebug
                 splitDiscontinuous
                 containedPlacement
                 happiness
                 intermediateUnitigs
                 setParentAndHang
                 stderr
  
  No output prefix name (-o option) supplied.
  No gatekeeper store (-G option) supplied.
  No overlap store (-O option) supplied.
  No output tigStore (-T option) supplied.
