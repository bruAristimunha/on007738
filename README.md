[![DOI](https://img.shields.io/badge/DOI-10.82901%2Fnemar.on007738-blue)](https://doi.org/10.82901/nemar.on007738)

Whole-Head Cocktail Party fNIRS

Whole-head functional near-infrared spectroscopy (fNIRS) recordings from
38 subjects performing covert and overt spatial-attention tasks in a
cocktail-party paradigm, with simultaneous eye-tracking.

fNIRS: 56 sources, 144 detectors, 1134 measurement channels at ~8.99 Hz.

Tasks
-----
overt:            Spatial attention with overt eye movements: subjects move
                  their eyes to attend to audiovisual stimuli (videos) on the
                  cued side.

covert:           Covert auditory attention: audio-only stimuli; subjects
                  fixate the central plus sign and attend to left or right
                  without moving their eyes.

visualorient:     Eye-movement-only baseline. Subjects make ~5 s eye orienting
                  and fixation movements with no audiovisual stimuli and no
                  fixation cross. Matches the overt task structure.

resting:          Resting-state recording: 5 minutes of central-fixation on a
                  plus sign with no task.

longvisualorient: Orienting + visual attention recording with events.tsv
                  aligned to the audiovisual orienting cue. Subjects orient
                  their eyes to the cue; ~15-17 s later a video clip appears
                  on the attended side. Same SNIRF recording as videoattend;
                  only the events.tsv differs.

videoattend:      Same SNIRF recording as longvisualorient, with events.tsv
                  aligned to the onset of the video clip (~15-17 s after the
                  orienting cue) for video-locked GLM analysis.

Privacy
-------
This dataset contains only fNIRS optical measurements and eye-tracking time
series; no anatomical scans (MRI, CT, photographs, or otherwise) are
included. Facial defacing is therefore not applicable to this dataset.
Data were acquired and shared under approved IRB consent.

Companion analysis code: https://github.com/duwadisudan/wholehead-cocktail-party-fnirs

## Known issues

Checked in the files of version 1.0.0; the source of each item is given with it.

- `sub-24/nirs/sub-24_task-visualorient_run-01_nirs.snirf` has no `/nirs/probe` group (no wavelengths, no optode
  positions; the file holds only `/nirs/data1` and `/nirs/metaDataTags`) and cannot be loaded by MNE-Python (source:
  the published file, sha256 c2462b88...a45130f as in its git-annex key).
- sub-32 covert run-02: 2 event onsets (614.3 s, 632.9 s) fall after the end of the recording (RecordingDuration
  597.635 s in its `_nirs.json`) and the event at 594.6 s (duration 5 s) runs past it (source: that run's
  events.tsv and nirs.json).
- sub-24 overt run-02 and sub-13 visualorient run-02 have no events.tsv (source: the file listing of this dataset).
- The events.tsv of the resting runs hold one row with trial_type n/a and duration 10 s (third column `amplitude` or
  `value` = 1); its meaning is not stated (source: the resting events.tsv files).
- The associated paper reports 43 recruited participants (26 in the main analysis, 8 returning for a control
  experiment) (doi:10.1016/j.neuroimage.2026.122292; text checked in its CC-BY preprint
  doi:10.1101/2026.05.06.722322, Methods, "Participants and Procedures"); this release holds 38 subject folders.
