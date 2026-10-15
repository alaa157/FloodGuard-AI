# Egypt Data-Readiness Checklist (FloodGuard AI - research only)

STATUS: data-readiness planning document. No Egyptian predictions were produced.

Study areas of interest: Sinai wadis, Red Sea Governorate coastal catchments.

Required before any Egypt experiment can be scientifically defensible:

[ ] 1. Hydrologically conditioned DEM (e.g. Copernicus GLO-30, ALOS AW3D30) on the model grid
[ ] 2. Historical storm catalog from NASA GPM IMERG Final (0.1 deg, 30 min, ~3.5-month latency),
      downscaled to the grid; Early/Late runs (4 h / 12 h latency) only for near-real-time experiments
[ ] 3. Wadi/channel network + infrastructure (culverts, dams); confidential gaps documented
[ ] 4. Reference water-depth labels: calibrated hydrodynamic simulations or validated observations
[ ] 5. Adaptation plan: few-shot fine-tuning of the released checkpoint (paper-supported) with documented splits
[ ] 6. Independent validation on held-out real events + baseline comparison
[ ] 7. Institutional coordination before any operational or public-facing use

Do NOT interpret LarNO benchmark performance (Shenzhen) as predictive skill in Egypt.
