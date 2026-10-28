# Station coordinate validation

The 27 October 2026 matched NaPTAN–BPLAN comparison contains 2,599 stations. Of these, 2,400 have plausible BPLAN coordinates and 199 have missing or implausible coordinates. Among plausible points the median separation is 64.031 m and 127 separations exceed 1 km.

Independent point-in-polygon assignments against official ONS December 2024 full-resolution LAD boundaries give 2,340 unchanged memberships and 43 changed memberships. Seventeen plausible BPLAN points cannot be assigned under both references. The 199 invalid or missing BPLAN points are also excluded from membership comparisons. No nearest-area substitution is used.

The comparison concerns the two coordinate references. All published geographic outputs use NaPTAN coordinates. Restricted BPLAN coordinates are not redistributed.

[The 43 changed assignments](../station-geocoding-checks/station-coordinate-changed-authorities.csv) list station names and the LAD codes and names under each coordinate reference. The machine-readable summary records the input comparison date. To reproduce a membership comparison from the corresponding authorised BPLAN snapshot and reviewed station mapping:

```bash
python src/02_validation.py --source RELEASE/processed --outdir RELEASE/validation \
  --bplan /path/to/authorised-bplan --lad-boundaries /path/to/official-lad-boundaries.geojson
```

Source: [ONS LAD December 2024 UK BFE boundaries](https://services1.arcgis.com/ESMARspQHYMw9BZ9/arcgis/rest/services/Local_Authority_Districts_December_2024_Boundaries_UK_BFE/FeatureServer/0). BPLAN access and attribution: [data sources](sources.md).

## Large-distance checks

The National Rail and council comparisons are documented manual checks, separate from the public pipeline. All 18 source comparisons exceeding 10 km were checked against the original BPLAN text records and station TIPLOCs, the current NaPTAN entries, and separately published station locations. Seventeen contain BPLAN coordinate errors; Langwith–Whaley Thorns has a BPLAN placeholder (99999 in both fields). The five-digit placeholder is excluded from the comparison sample.

[The station-level review](../station-geocoding-checks/station-large-distance-review.csv) records sources and distances. NaPTAN is within 147 m of the corroborating location in every reviewed case. National Rail station-map links corroborate 17 locations. For Laurencekirk, the National Rail map link is about 1.2 km from NaPTAN; Aberdeenshire Council's station record at grid NO 7170 7180 is within 5 m of NaPTAN and supports its location.

The large-distance failures do not imply NaPTAN assignment errors. The 43 LAD differences describe disagreement between coordinate references, including ordinary differences near authority boundaries. They are not a count of erroneous NaPTAN locations.
