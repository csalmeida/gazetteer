# Gazetteer

A library that can be used to list all 249 countries and territories.

## Features

- Provides comprehensive information about countries and territories
- Easy to use API for accessing country data
- Includes ISO codes, region information, and more

## Country Struct

The `Country` struct contains the following fields:

- `name`: String - The full name of the country
- `alpha_2`: String - The ISO 3166-1 alpha-2 code (two-letter country code)
- `alpha_3`: String - The ISO 3166-1 alpha-3 code (three-letter country code)
- `country_code`: u16 - The numeric country code
- `iso_3166_2`: Option<String> - The ISO 3166-2 code for principal subdivisions (e.g., provinces or states)
- `region`: String - The geographical region the country belongs to
- `region_code`: Option<u16> - The numeric code for the region
- `sub_region`: String - The geographical sub-region the country belongs to
- `sub_region_code`: Option<u16> - The numeric code for the sub-region
- `intermediate_region`: Option<String> - An optional intermediate region classification
- `intermediate_region_code`: Option<u16> - The numeric code for the intermediate region, if applicable

This struct provides a comprehensive representation of a country, including various standardized codes and geographical classifications.

## Development

```console
cargo build
```

```console
cargo test
```

Documentation:

```console
cargo doc --open
```
