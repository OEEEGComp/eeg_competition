---
layout: default
---

# Short description

The dataset is a mobile EEG collection focused on motor execution tasks using an xbox controller. Collected from 26 participants across 127 sessions, it includes synchronized EEG recordings, stimulus and game controller trigger data. The experiments employed the g.tec Unicorn EEG headset with eight electrodes positioned over sensorimotor and occipital regions and sampled at 250 Hz. Participants executed specific tasks such as left, right, or dual finger movements, or remaining idle, following auditory and visual cues. The dataset was preprocessed with bandpass filtering (0.5–50 Hz) and epoch segmentation.

# Detailed description

The experiment followed a structured design: a baseline phase (eyes-open, eyes-closed, and random eye movements) was followed by motor execution trials, each initiated by an auditory warning and a visual cue. Tasks were recorded with synchronization using the Lab Streaming Layer to ensure temporal accuracy between EEG and trigger pull signals. Preprocessing included bandpass filtering (0.5–50 Hz), removing trials where the reaction time was slower than 0.6 seconds and epoching around cue and trigger events.

# Data structure

The training contains 20 `.h5` and `.pickle` file pairs, each representing a participant’s trial data and its metadata. The test data is built up from 8 file pairs.

## H5 file structure for train

- **epochs_on_break:** Epoched time intervals between trials
- **epochs_on_pull:** Epoched pulling trials
- **epochs_on_task:** All epoched trials
- **event_session_idx:** Describes which session the Nth event belongs to
- **events:** All event starts
- **filt_raw_eeg_n:** Nth session filtered EEG signal (non-epoched)
- **gamepad_n:** Nth session filtered gamepad signal (non-epoched)
- **on_break_events:** Break event start
- **on_break_session_idx:** Session index for break events
- **on_pull_events:** Pull event start
- **on_pull_session_idx:** Session index for pull events
- **on_task_events:** Trial event start
- **on_task_session_idx:** Session index for trial events

## Pickle structure

- **eeg_info:** Basic information of the setup
- **event_dict:** Event code meanings
- *Additional details:* Information about filtering and preprocessing

*Note:* The test data does not contain annotations.

# Output format

The output format is as described in the provided `output_format.ipynb`. Each participant should have a `.h5` file containing the predicted class, and the class encoding should be saved to the file.

