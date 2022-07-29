The FITS file in this directory was generated using the following ADQL query:

```sql
SELECT
    gaia_source.source_id,gaia_source.ra,gaia_source.dec,
    gaia_source.parallax,gaia_source.parallax_error,
    gaia_source.phot_g_mean_mag,gaia_source.bp_rp,
    gaia_source.nu_eff_used_in_astrometry,gaia_source.pseudocolour,
    gaia_source.ecl_lat, gaia_source.astrometric_params_solved
FROM gaiadr3.gaia_source
WHERE
    gaia_source.parallax IS NOT NULL
    AND CONTAINS(
        POINT('ICRS',gaiadr3.gaia_source.ra,gaiadr3.gaia_source.dec),
        CIRCLE(
            'ICRS',
            COORD1(EPOCH_PROP_POS(132.846,11.814,1.1325,-10.9737,-2.9396,33.9200,2000,2016.0)),
            COORD2(EPOCH_PROP_POS(132.846,11.814,1.1325,-10.9737,-2.9396,33.9200,2000,2016.0)),
            0.5)
    )=1
```
