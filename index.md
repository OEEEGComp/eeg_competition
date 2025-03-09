---
layout: default
---
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Mobile EEG Dataset of Game Controller Use</title>
  <style>
    body {
      font-family: 'Helvetica Neue', Helvetica, Arial, sans-serif;
      margin: 0;
      padding: 0;
      background: #f4f4f9;
      color: #333;
      line-height: 1.6;
    }
    .container {
      max-width: 900px;
      margin: 2rem auto;
      padding: 2rem;
      background: #fff;
      border-radius: 5px;
      box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    }
    h1, h2 {
      color: #2c3e50;
    }
    h1 {
      border-bottom: 2px solid #2c3e50;
      padding-bottom: 0.5rem;
    }
    p {
      margin: 1rem 0;
    }
    ul {
      margin-left: 1.5rem;
    }
    a {
      display: inline-block;
      margin-top: 1.5rem;
      text-decoration: none;
      color: #3498db;
      border: 1px solid #3498db;
      padding: 0.5rem 1rem;
      border-radius: 5px;
      transition: background 0.3s, color 0.3s;
    }
    a:hover {
      background: #3498db;
      color: #fff;
    }
    code {
      background: #eee;
      padding: 2px 4px;
      border-radius: 3px;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>Mobile EEG Dataset of Game Controller Use</h1>

    <h2>Short description</h2>
    <p>
      The dataset is a mobile EEG collection focused on motor execution tasks using an xbox controller. Collected from 26 participants across 127 sessions, it includes synchronized EEG recordings, stimulus and game controller trigger data. The experiments employed the g.tec Unicorn EEG headset with eight electrodes positioned over sensorimotor and occipital regions and sampled at 250 Hz. Participants executed specific tasks such as left, right, or dual finger movements, or remaining idle, following auditory and visual cues. The dataset was preprocessed with bandpass filtering (0.5–50 Hz) and epoch segmentation.
    </p>

    <h2>Detailed description</h2>
    <p>
      The experiment followed a structured design: a baseline phase (eyes-open, eyes-closed, and random eye movements) was followed by motor execution trials, each initiated by an auditory warning and a visual cue. Tasks were recorded with synchronization using the Lab Streaming Layer to ensure temporal accuracy between EEG and trigger pull signals. Preprocessing included bandpass filtering (0.5–50 Hz), removing trials with a reaction time slower than 0.6 seconds, and epoching around cue and trigger events.
    </p>

    <h2>Data structure</h2>
    <p>
      The training contains 20 .h5 and .pickle file pairs, each representing a participant’s trial data and its metadata. The test data is built up from 8 file pairs.
    </p>
    <p>
      <strong>H5 file structure for train:</strong>
      <ul>
        <li>epochs_on_break: Epoched time intervals between trials</li>
        <li>epochs_on_pull: Epoched pulling trials</li>
        <li>epochs_on_task: All epoched trials</li>
        <li>event_session_idx: Session index for each event</li>
        <li>events: All event starts</li>
        <li>filt_raw_eeg_n: Nth session filtered EEG signal (non-epoched)</li>
        <li>gamepad_n: Nth session filtered gamepad signal (non-epoched)</li>
        <li>on_break_events: Break event start</li>
        <li>on_break_session_idx: Session index for break events</li>
        <li>on_pull_events: Pull event start</li>
        <li>on_pull_session_idx: Session index for pull events</li>
        <li>on_task_events: Trial event start</li>
        <li>on_task_session_idx: Session index for trial events</li>
        <li>tfr_epochs_on_break: Multitaper time-frequency representation of breaks</li>
        <li>tfr_epochs_on_pull: Multitaper time-frequency representation of pull events</li>
        <li>tfr_epochs_on_task: Multitaper time-frequency representation of trial events</li>
      </ul>
    </p>
    <p>
      <strong>Pickle structure:</strong>
      <ul>
        <li>eeg_info: Basic information of the setup</li>
        <li>event_dict: Event code meanings</li>
        <li>Additional filtering and preprocessing information</li>
      </ul>
    </p>
    <p>
      <strong>Note:</strong> Test data does not include annotations.
    </p>

    <h2>Output format</h2>
    <p>
      The output format is as described in the provided <code>output_format.ipynb</code>. Each participant should have a .h5 file containing the predicted class. Also, save the class encoding to the file!
    </p>
  </div>
</body>
</html>