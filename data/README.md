# Geolocation metadata

This release contains **2,207 unique panorama IDs across 56 country labels**.

- [`pano_ids.csv`](pano_ids.csv): `sample_id,pano_id` index.
- [`annotations/geolocalization.json`](annotations/geolocalization.json): country, city, street and latitude/longitude labels, linked by sample ID and pano ID.
- [`metadata.json`](metadata.json): field definitions, counts and release scope.
- [`SHA256SUMS`](SHA256SUMS): data checksums.

Sample IDs are release-local identifiers. No official train/validation/test split is assigned. Labels are preserved from source metadata without inference; missing city/street labels remain empty. One duplicate demo record was merged, retaining nonempty labels. These assets are geolocation metadata, not FP/SA/CS question annotations.

Raw Street View imagery is not redistributed. Retrieve imagery using your own credentials and comply with the original provider's applicable terms. Never commit credentials or credential-bearing download URLs.

Evaluation and inference scripts in this repository remain placeholders; this metadata release does not make them executable evaluators.
