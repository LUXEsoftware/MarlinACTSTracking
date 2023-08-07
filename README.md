# MarlinACTSTracking
Marlin-based ACTS Tracking adapted from MuonColliderSoft


`luxegeo` should be installed.
To setup, do
```bash
source /cvmfs/ilc.desy.de/key4hep/luxe_setup.sh
source ../luxegeo/install/bin/thisluxegeo.sh
```

``bash
mkdir build
cd build
cmake .. -DCMAKE_BUILD_TYPE=RelWithDebInfo -DCMAKE_INSTALL_PREFIX=../install
make install
export MARLIN_DLL=$(echo ${MARLIN_DLL}':install/lib/libMarlinACTSTracking.so')
```
To run combinatorial Kalman Filter tracking:
```bash
Marlin actsseedckf_steer.xml
```

## Digitisation only
This runs simple tracker digitisation by smearing the true hit position with a Gaussian function. Output includes an ntuple and optionally an ACTS-compatible CSV format.

To run digitisation:
```bash
Marlin digi_steer.xml
```

## Optional: output in CSV format 
```bash
git clone ssh://git@gitlab.cern.ch:7999/berkeleylab/MuonCollider/ACTSTuple.git
cd ACTSTuple
mkdir build
cmake -S . -B build
cmake --build build
export MARLIN_DLL=$(echo ${MARLIN_DLL}':build/libACTSTuple.so')
```
Run with `MyACTSTuple` processor uncommented in `digi_steer.xml`

