# Trigger Short Exercise 2025
Trigger short exercise CMS DAS @ LPC FNAL, January 2025 ([Indico](https://indico.cern.ch/event/1388937/))

Slides can be found [here]()

Please join our Mattermost channel for Q&A ([link]())

## Facilitators
1. Dener De Souza Lemos

## Setup
Both lxplus8 and lxplus9 can be used
```
ssh username@lxplus.cern.ch
```
CMSSW Setup:
```    
source /cvmfs/cms.cern.ch/cmsset_default.sh
mkdir CMSDAS2025
cd CMSDAS2025
cmsrel CMSSW_14_0_8
cd CMSSW_14_0_8/src
cmsenv
git clone https://gitlab.cern.ch/cmsdas-cern-2024/short-ex-triggers.git
scram b -j 4
cd short-ex-triggers
```

## Exercise 1
### Measure the MET triggers efficiencies
```
python3 test/MET_Efficiency_NanoAOD.py          # running over full 2023D EGamma0 NanoAOD datasets
root -l --web=off histos_METTrigNanoAOD.root    # check histograms out
python3 test/MET_Efficiency_Plotting.py         # plotting
```

## Exercise 2
### Measure the SingleMuon triggers efficiencies using the same method
Similar to ex1, you can draw efficiencies vs. pt like (IsoMu24, Mu50, CascadeMu100, HighPtTkMu100, ALL)

Please try to do it with your own codes, you can use codes from ex1.

If you want to draw their efficiencies vs. eta, phi, then you may need to apply pt cut to offline muons (eg. pt > 26 GeV for IsoMu24)

Try it with less input files first.


<details>
    <summary><i>In case you need help, here's our example</i></summary>

```
python3 test/SingleMuon_Efficiency_NanoAOD_answerEx2.py   # running over partial 2023D EGamma0 NanoAOD datasets
root -l --web=off histos_SingleMuTrigNanoAOD.root         # check histograms out
python3 test/SingleMuon_Efficiency_Plotting_answerEx2.py  # plotting
```
</details>

## Exercise 3
### Measure the SingleMuon (IsoMu24) trigger efficiency using the Tag & Probe
```
python3 test/SingleMuon_Efficiency_TnP_NanoAOD.py           # running over full 2023Dv2 Muon0 NanoAOD datasets
root -l --web=off histos_SingleMuTrigNanoAOD_TnP.root       # check histograms out
python3 test/SingleMuon_Efficiency_TnP_Plotting_NanoAOD.py  # plotting
```

## Exercise 4 (Optional)
### Measure the SingleMuon (Mu50 || CascadeMu100 || HighPtTkMu100) trigger efficiency
The trigger indexes for Mu50, Mu100s are 10, 11. See this [cms-sw](https://github.com/cms-sw/cmssw/blob/master/PhysicsTools/NanoAOD/python/triggerObjects_cff.py#L109-L131)

## In case gio doesn't work for you
you can bring the files to your local machine
```
# in your local machine
scp lxplus.cern.ch:<path>/<to>/<my_directory>/*.pdf .
```
or you can open it via cernbox: https://cernbox.cern.ch/
```
cd /eos/user/<initial>/<username>/
mkdir CMSDAS2025
cd -  # working directory used for trigger exercise
cp *.pdf /eos/user/<initial>/<username>/CMSDAS2025
```

## References or useful links
Twiki of Trigger exercise of CMS DAS @ CERN 2023 : [link](https://twiki.cern.ch/twiki/bin/viewauth/CMS/SWGuideCMSDataAnalysisSchoolCERN2023TriggerExercise)

HLT Tutorials in 2024 : [link](https://indico.cern.ch/event/1344500/)

HLT Tutorials in 2023 : [link](https://indico.cern.ch/event/1238936/)

Trigger exercise for the PO & DAS 2023 @ Hamburg : [link](https://gitlab.cern.ch/cms-analysis/cmsdas/dpg/trigger-exercise)
