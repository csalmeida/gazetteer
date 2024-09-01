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

## Usage

Add the crate as a dependency:

```console
cargo add gazetteer
```

A few examples of how to use the Gazetteer's methods:

```rust
use gazetteer::countries;

fn main() {
    // Get all countries
    let all_countries = countries::all();
    println!("Total number of countries: {}", all_countries.len());

    // Find a country by its alpha-2 code
    let usa = countries::find_by(|c| c.alpha_2 == "US").unwrap();
    println!("Country name: {}", usa.name);
    println!("Alpha-3 code: {}", usa.alpha_3);
    println!("Country code: {}", usa.country_code);

    // Find a country by its name
    let japan = countries::find_by(|c| c.name == "Japan").unwrap();
    println!("Japan's region: {}", japan.region);
    println!("Japan's sub-region: {}", japan.sub_region);

    // Find countries in a specific region
    let european_countries: Vec<_> = countries::all()
        .into_iter()
        .filter(|c| c.region == "Europe")
        .collect();
    println!("Number of European countries: {}", european_countries.len());

    // Find a country by its numeric code
    let france = countries::find_by(|c| c.country_code == 250).unwrap();
    println!("Country with code 250: {}", france.name);

    // Check if a country has an intermediate region
    let brazil = countries::find_by(|c| c.alpha_3 == "BRA").unwrap();
    if let Some(region) = &brazil.intermediate_region {
        println!("Brazil's intermediate region: {}", region);
    } else {
        println!("Brazil has no intermediate region");
    }
}
```
