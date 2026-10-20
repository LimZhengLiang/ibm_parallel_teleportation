# Parallel Teleportation via AME(5,2) States on IBM Quantum Hardware

Notebooks and selected experimental data for two-channel quantum teleportation using a five-qubit absolutely maximally entangled state, AME(5,2). The experiments compare decoder ranks 1 and 58, dynamical decoupling settings, and classical Pauli frame post-processing versus real-time feedforward.

## Repository contents

- `main_scripts/`: Jupyter notebooks for hardware experiments, stage diagnostics and decoder synthesis.
- `data/`: selected experimental data archives, with classical post-processing and feedforward data kept separate.

## Notebooks

| Notebook | Purpose |
| --- | --- |
| [Rank 1 cascade](main_scripts/NEWv5_MCM_CLASSICAL_R456_RANK1.ipynb) | Hardware reference–receiver entanglement fidelity at R0–R3, using classical post-processing. |
| [Rank 58 cascade](main_scripts/NEWv2MCM_SHARED_PREPARATION_RANK58_TEST_NEWv7_V5_M3_DIRECT_CHSH.ipynb) | Corresponding R0–R3 experiments with the rank-58 decoder. |
| [Rank 1 stage diagnostics](main_scripts/ame52_full_extended_analysis_v13_mcm_rank1_v044_TEST.ipynb) | Tomography, stabilizer-generator witnesses, SWAP tests and Bell-outcome-conditioned receiver analysis. |
| [Rank 58 decoding diagnostics](main_scripts/rank58_v234former_stage2_v044_TEST.ipynb) | Stage-2 characterisation after AME preparation and rank-58 decoding. |
| [Decoder synthesis](main_scripts/synthesize_W012_dagger_same_AME_rank58verified.ipynb) | Offline search, verification and logical-cost ranking of compact Clifford decoders. No QPU access is required. |

Some filenames are historical: the supplied NEWv2 notebooks are fidelity-only despite mentioning CHSH, and the NEWv4 notebooks currently acquire R4 and R5, not R6.

## Running the notebooks

1. Open the chosen notebook in Jupyter using a compatible Python environment. Dependencies include Qiskit, Qiskit IBM Runtime, Qiskit Experiments, Qiskit Aer, M3 (`mthree`), Mapomatic, NumPy, SciPy, pandas and Matplotlib. The NEWv2 and NEWv4 notebooks require `qiskit-ibm-runtime==0.43.0`.
2. For hardware acquisition, configure your IBM Quantum account locally and review the backend, shot count, number of trials, DD policies and optimisation settings. The supplied acquisition notebooks currently use `N_TRIALS=1`.
3. Review all hardware submission cells before using **Run All**. Several supplied notebooks already have `RUN_EXPERIMENT=True`. Enable hardware execution only when you intend to submit QPU jobs.

Do not upload API tokens, credentials or private information, including information saved in notebook outputs.

## Experimental data

The selected classical data archives contain individual trial folders with `opt_level_2_records.csv` and `opt_level_3_records.csv`. These include both raw and M3 readout-mitigated estimates; no hardware access is needed to inspect them.

For comparisons, select the correction method, decoder rank, channel, DD sequence, optimisation level, processing method and round before averaging. The manuscript summaries use equal-weight means over eight selected trials per rank. Do not pool classical and feedforward records or count raw and M3 estimates as independent trials.

New hardware runs may produce different results because backend calibrations, layouts and compiled circuits can change.

## Reference 
