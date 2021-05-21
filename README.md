# Actor - Crunchbase Scraper

## Crunchbase scraper

Since Crunchbase doesn't provide a proper and free API, this actor should help you to retrieve data from it.

The Crunchbase data scraper supports the following features:

- Scrape organization details - You can scrape attributes like about, number of employees, technology, summary, people working or investment details of an organization. You can find details below.

- Scrape person details - You can scrape attributes like title, name, CB Rank, primary organization, jobs or related hubs of a person. You can find details below.

- Scrape event details - You can scrape attributes like speakers, name, location, date, venue and registration links of an event. You can find details below.

- Scrape hub details - You can scrape attributes like number of founders, name, founded date, acquired percentage and so on. You can find details below.

- Scrape by keyword - You can use location-wise keywords to search specific search lists. Also you can directly point out rental, for sale or sold properties on this feature.


## Bugs, fixes, updates and changelog
This scraper is under active development. If you have any feature requests you can create an issue from [here](https://github.com/tugkan/crunchbase-scraper/issues).

### Incoming Changes
- Advanced search


## Input Parameters

The input of this scraper should be JSON containing the list of pages on Crunchbase that should be visited. Required fields are:

| Field | Type | Description |
| ----- | ---- | ----------- |
| startUrls | Array | (optional) List of Crunchbase URLs. You should only provide organization detail, person detail, event detail or hub detail URLs |
| search | String | (optional) Keyword that can be searched in Crunchbase search engine. When it is present, `mode` must be used as well. |
| mode | String | (optional) Mode of the actor. It gets the keyword from `search` parameter and initiate the search according to the mode. Can be `all`, `organizations`, `events`, `hubs` or `people`. When present, `search` must be provided as well. |
| maxItems | Integer | (optional) You can limit scraped items.
| proxy | Object | Proxy configuration |
This solution requires the use of **Proxy servers**, either your own proxy servers or you can use <a href="https://www.apify.com/docs/proxy">Apify Proxy</a>.


### Compute Unit Consumption
The actor optimized to run blazing fast and scrape many as properties as possible. Therefore, it forefronts all property detail requests. If actor doesn't block very often it'll scrape 50 items in 2 minutes with ~0.05-0.07 compute units.

### Crunchbase Scraper Input example
```json
{
  "startUrls":[
    {"url":"https://www.crunchbase.com/person/warner-l-baxter"},
    {"url":"https://www.crunchbase.com/organization/warner-law-offices"}
  ],
  "search":"warner",
  "proxy": {
    "useApifyProxy": true
  },
  "mode": "all",
  "maxItems": 500
}

```

## During the Run

During the run, the actor will output messages letting you know what is going on. Each message always contains a short label specifying which page from the provided list is currently specified.
When items are loaded from the page, you should see a message about this event with a loaded item count and total item count for each page.

If you provide incorrect input to the actor, it will immediately stop with failure state and output an explanation of what is wrong.

## Crunchbase Export

During the run, the actor stores results into a dataset. Each item is a separate item in the dataset.

You can manage the results in any languague (Python, PHP, Node JS/NPM). See the FAQ or <a href="https://www.apify.com/docs/api" target="blank">our API reference</a> to learn more about getting results from this Crunchbase actor.

## Scraped Crunchbase Items
The structure of each item in Crunchbase items looks like this:

### Person

```json
{
  "properties": {
    "identifier": {
      "uuid": "27e940be-6f97-2ee0-b8a9-5896fc45bc2a",
      "value": "Warner L. Baxter",
      "image_id": "v1460807093/enb7lpjnglfxlapctkkp.png",
      "permalink": "warner-l-baxter",
      "entity_def_id": "person"
    },
    "facet_ids": [
      "rank"
    ],
    "title": "Warner L. Baxter - Chairman, President and Chief Executive Officer @ Ameren Services",
    "short_description": "Business Experience:Mr. Baxter, 54, is the Chairman, President and Chief Executive Officer of Ameren Corporation, a regulated electric and g..."
  },
  "cards": {
    "education_summary": {
      "identifier": {
        "uuid": "27e940be-6f97-2ee0-b8a9-5896fc45bc2a",
        "value": "Warner L. Baxter",
        "image_id": "v1460807093/enb7lpjnglfxlapctkkp.png",
        "permalink": "warner-l-baxter",
        "entity_def_id": "person"
      }
    },
    "current_board_and_advisory_roles_image_list": [
      {
        "identifier": {
          "uuid": "4dbd38e5-3f9b-9d0b-4c8a-e2c71e2f7d41",
          "value": "Warner L. Baxter Board of Director @ Ameren Services",
          "permalink": "warner-l-baxter-board-member-ameren--4dbd38e5",
          "entity_def_id": "job"
        },
        "organization_identifier": {
          "uuid": "fa3d8616-afc6-abc5-c103-a7a1074eeb79",
          "value": "Ameren Services",
          "image_id": "v1402650462/arrtxhwudi5syoqleyqe.png",
          "permalink": "ameren",
          "entity_def_id": "organization"
        },
        "title": "Board of Director"
      },
      {
        "identifier": {
          "uuid": "ce8f5c6f-6e3c-4d4c-b0a0-c1a5d8ab3e6f",
          "value": "Warner L. Baxter Board Of Director @ U.S. Bancorp",
          "permalink": "warner-l-baxter-board-member-u-s-bancorp--ce8f5c6f",
          "entity_def_id": "job"
        },
        "organization_identifier": {
          "uuid": "9561f613-9cc0-d418-da8c-2f545b6eb8b6",
          "value": "U.S. Bancorp",
          "image_id": "v1397179096/f5615a5f64426ad47ec9c4e43409a1bf.png",
          "permalink": "u-s-bancorp",
          "entity_def_id": "organization"
        },
        "title": "Board Of Director"
      }
    ],
    "current_jobs_image_list": [
      {
        "identifier": {
          "uuid": "7aba5665-f138-df29-c604-b32415e569e1",
          "value": "Warner L. Baxter Chairman, President and Chief Executive Officer @ Ameren Services",
          "permalink": "warner-l-baxter-employee-ameren--7aba5665",
          "entity_def_id": "job"
        },
        "organization_identifier": {
          "uuid": "fa3d8616-afc6-abc5-c103-a7a1074eeb79",
          "value": "Ameren Services",
          "image_id": "v1402650462/arrtxhwudi5syoqleyqe.png",
          "permalink": "ameren",
          "entity_def_id": "organization"
        },
        "title": "Chairman, President and Chief Executive Officer"
      }
    ],
    "board_and_advisory_roles_summary": {
      "identifier": {
        "uuid": "27e940be-6f97-2ee0-b8a9-5896fc45bc2a",
        "value": "Warner L. Baxter",
        "image_id": "v1460807093/enb7lpjnglfxlapctkkp.png",
        "permalink": "warner-l-baxter",
        "entity_def_id": "person"
      },
      "num_current_advisor_jobs": 2
    },
    "overview_fields2": {},
    "past_jobs_list": [],
    "overview_fields_v2": {
      "primary_job_title": "Chairman, President and Chief Executive Officer",
      "primary_organization": {
        "uuid": "fa3d8616-afc6-abc5-c103-a7a1074eeb79",
        "value": "Ameren Services",
        "image_id": "v1402650462/arrtxhwudi5syoqleyqe.png",
        "permalink": "ameren",
        "entity_def_id": "organization"
      }
    },
    "past_board_and_advisory_roles_list": [],
    "overview_fields": {
      "gender": "male"
    },
    "jobs_summary": {
      "identifier": {
        "uuid": "27e940be-6f97-2ee0-b8a9-5896fc45bc2a",
        "value": "Warner L. Baxter",
        "image_id": "v1460807093/enb7lpjnglfxlapctkkp.png",
        "permalink": "warner-l-baxter",
        "entity_def_id": "person"
      },
      "num_current_jobs": 1
    },
    "overview_description": {
      "description": "Business Experience:Mr. Baxter, 54, is the Chairman, President and Chief Executive Officer of Ameren Corporation, a regulated electric and gas utility company serving customers in Missouri and Illinois. He has served in these positions since 2014. Mr. Baxter served as Chairman, President and Chief Executive Officer of Ameren Missouri from 2009 to 2014 and as Executive Vice President and Chief Financial Officer of Ameren Corporation from 2003 to 2009. In addition, he also served as President and Chief Executive Officer of Ameren Services from 2007 to 2009."
    },
    "board_and_advisory_roles_headline": {
      "num_current_advisor_jobs": 2
    },
    "overview_headline": {
      "num_current_advisor_jobs": 2,
      "rank_person": 104129
    },
    "news_headline": {
      "num_articles": 9
    },
    "event_appearances_summary": {
      "identifier": {
        "uuid": "27e940be-6f97-2ee0-b8a9-5896fc45bc2a",
        "value": "Warner L. Baxter",
        "image_id": "v1460807093/enb7lpjnglfxlapctkkp.png",
        "permalink": "warner-l-baxter",
        "entity_def_id": "person"
      }
    },
    "education_image_list": [],
    "event_appearances_list": [],
    "hubs_list": [
      {
        "identifier": {
          "permalink": "electrical-distribution-companies",
          "image_id": "qunvrh1ipdxiveejujcq",
          "uuid": "3cbc8c65-6619-4954-967c-978ca8cc17d8",
          "entity_def_id": "hub",
          "value": "Electrical Distribution Companies"
        },
        "rank_hub": 2391
      },
      {
        "identifier": {
          "permalink": "solar-companies",
          "image_id": "qxktzxyjyoo3ojtsv1cj",
          "uuid": "b209864f-5f74-447f-b7f5-4d91e1573fcb",
          "entity_def_id": "hub",
          "value": "Solar Companies"
        },
        "rank_hub": 3738
      },
      {
        "identifier": {
          "permalink": "energy-public-companies",
          "image_id": "v1488039292/yesmtc8tpggbkfvfakjj.png",
          "uuid": "d628bfb1-0955-4d52-81a6-0792c5768474",
          "entity_def_id": "hub",
          "value": "Energy Public Companies"
        },
        "rank_hub": 5594
      },
      {
        "identifier": {
          "permalink": "electrical-distribution-public-companies",
          "image_id": "v1470302873/fgmqdg1rqbrfqningev0.png",
          "uuid": "f3a7290e-c6f1-446a-a20a-5f19cae814e5",
          "entity_def_id": "hub",
          "value": "Electrical Distribution Public Companies"
        },
        "rank_hub": 23763
      },
      {
        "identifier": {
          "permalink": "oil-and-gas-companies",
          "image_id": "v1488039292/yesmtc8tpggbkfvfakjj.png",
          "uuid": "abf2ae9a-ee16-4232-957b-9da73fdcc902",
          "entity_def_id": "hub",
          "value": "Oil and Gas Companies"
        },
        "rank_hub": 884
      },
      {
        "identifier": {
          "permalink": "oil-and-gas-companies-that-exited",
          "image_id": "v1488039292/yesmtc8tpggbkfvfakjj.png",
          "uuid": "311c6486-7c4f-4166-99fc-479b88410bd1",
          "entity_def_id": "hub",
          "value": "Oil and Gas Companies that Exited"
        },
        "rank_hub": 3550
      },
      {
        "identifier": {
          "permalink": "energy-companies-that-exited",
          "image_id": "v1488039292/yesmtc8tpggbkfvfakjj.png",
          "uuid": "6edc42a8-c17d-4725-b5ec-1fbc79f80d3c",
          "entity_def_id": "hub",
          "value": "Energy Companies that Exited"
        },
        "rank_hub": 2659
      },
      {
        "identifier": {
          "permalink": "electrical-distribution-companies-that-exited",
          "image_id": "v1470302873/fgmqdg1rqbrfqningev0.png",
          "uuid": "1a73b0ae-6105-4d96-b3bc-253514629c5b",
          "entity_def_id": "hub",
          "value": "Electrical Distribution Companies that Exited"
        },
        "rank_hub": 10515
      },
      {
        "identifier": {
          "permalink": "solar-companies-that-exited",
          "image_id": "m06tssvwea7mcbya02ik",
          "uuid": "05acd309-af54-44bd-9c37-7de789c86271",
          "entity_def_id": "hub",
          "value": "Solar Companies that Exited"
        },
        "rank_hub": 18733
      },
      {
        "identifier": {
          "permalink": "consumer-electronics-companies-that-exited",
          "image_id": "v1475583702/sjuchl5dc4p56li5qlxj.png",
          "uuid": "4813123b-b076-4d83-802b-99224e06de25",
          "entity_def_id": "hub",
          "value": "Consumer Electronics Companies that Exited"
        },
        "rank_hub": 9097
      }
    ],
    "jobs_headline": {
      "num_current_jobs": 1
    },
    "event_appearances_headline": {}
  }
}
```

### Organization
```json
{
  "properties": {
    "identifier": {
      "uuid": "659eff91-c557-46a9-8655-66289b4ab451",
      "value": "Warner",
      "image_id": "wmlnt4ssvplwk2snjlvg",
      "permalink": "warner-law-offices",
      "entity_def_id": "organization"
    },
    "short_description": "Warner is a personal injury firm that offers miners, loggers, construction and other workers in personal injury & wrongful death litigation.",
    "title": "Warner",
    "facet_ids": [
      "aberdeen",
      "company",
      "rank",
      "builtwith",
      "bombora",
      "key_event"
    ]
  },
  "cards": {
    "semrush_summary": {
      "identifier": {
        "uuid": "659eff91-c557-46a9-8655-66289b4ab451",
        "value": "Warner",
        "image_id": "wmlnt4ssvplwk2snjlvg",
        "permalink": "warner-law-offices",
        "entity_def_id": "organization"
      }
    },
    "company_about_fields1": {},
    "current_advisors_image_list": [],
    "recommended_search": [
      {
        "org_num": 1517,
        "queries": {
          "person": [
            {
              "field_id": "location_identifiers",
              "operator_id": "includes",
              "values": [
                "f110fca2-1055-99f6-996d-011c198b3928"
              ],
              "type": "predicate"
            },
            {
              "collection_id": "organization.has_primary_organization.forward",
              "query": [
                {
                  "field_id": "facet_ids",
                  "operator_id": "includes",
                  "values": [
                    "company"
                  ],
                  "type": "predicate"
                },
                {
                  "field_id": "location_identifiers",
                  "operator_id": "includes",
                  "values": [
                    "f110fca2-1055-99f6-996d-011c198b3928"
                  ],
                  "type": "predicate"
                },
                {
                  "field_id": "categories",
                  "operator_id": "includes",
                  "values": [
                    "98de1ee2-4c3b-be26-0f7b-46fddbbfe76d"
                  ],
                  "type": "predicate"
                },
                {
                  "field_id": "operating_status",
                  "operator_id": "eq",
                  "values": [
                    "active"
                  ],
                  "type": "predicate"
                }
              ],
              "type": "sub_query"
            }
          ],
          "organization": [
            {
              "field_id": "facet_ids",
              "operator_id": "includes",
              "values": [
                "company"
              ],
              "type": "predicate"
            },
            {
              "field_id": "location_identifiers",
              "operator_id": "includes",
              "values": [
                "f110fca2-1055-99f6-996d-011c198b3928"
              ],
              "type": "predicate"
            },
            {
              "field_id": "categories",
              "operator_id": "includes",
              "values": [
                "98de1ee2-4c3b-be26-0f7b-46fddbbfe76d"
              ],
              "type": "predicate"
            },
            {
              "field_id": "operating_status",
              "operator_id": "eq",
              "values": [
                "active"
              ],
              "type": "predicate"
            }
          ],
          "event": [
            {
              "field_id": "location_identifiers",
              "operator_id": "includes",
              "values": [
                "f110fca2-1055-99f6-996d-011c198b3928"
              ],
              "type": "predicate"
            },
            {
              "field_id": "categories",
              "operator_id": "includes",
              "values": [
                "98de1ee2-4c3b-be26-0f7b-46fddbbfe76d"
              ],
              "type": "predicate"
            },
            {
              "collection_id": "principal.has_event.forward",
              "query": [
                {
                  "field_id": "facet_ids",
                  "operator_id": "includes",
                  "values": [
                    "company"
                  ],
                  "type": "predicate"
                },
                {
                  "field_id": "operating_status",
                  "operator_id": "eq",
                  "values": [
                    "active"
                  ],
                  "type": "predicate"
                }
              ],
              "type": "sub_query"
            }
          ]
        },
        "identifier": {
          "permalink": "united-states-law-enforcement-companies",
          "image_id": "iaspgmejgo3mfn9uvcyh",
          "uuid": "313732db-0534-40b2-a536-ff023b7c3a1a",
          "entity_def_id": "hub",
          "value": "United States Law Enforcement Companies"
        },
        "org_identifiers": [
          {
            "permalink": "mark43",
            "image_id": "iaspgmejgo3mfn9uvcyh",
            "uuid": "3904146d-13d9-65c6-6993-78a8ac2bdada",
            "entity_def_id": "organization",
            "value": "Mark43"
          },
          {
            "permalink": "shotspotter",
            "image_id": "v1499876060/wugvok8mc0tnjk7828a1.png",
            "uuid": "adef12da-172c-a287-777b-781e1e77fa8b",
            "entity_def_id": "organization",
            "value": "ShotSpotter"
          },
          {
            "permalink": "casetext",
            "image_id": "mbfrvby8uk1ctxwyqctp",
            "uuid": "8730f8f9-7a67-2f96-ae78-afcbdd87754a",
            "entity_def_id": "organization",
            "value": "Casetext"
          },
          {
            "permalink": "university-of-louisville",
            "image_id": "v1481520408/w3m76fmjz5iwkowmhwzh.png",
            "uuid": "5694fe70-18e3-ed37-b526-5520462d7522",
            "entity_def_id": "organization",
            "value": "University of Louisville"
          },
          {
            "permalink": "grayshift",
            "image_id": "c19xgpdu1r5jc78lq6ef",
            "uuid": "a7bffc64-f7fe-49fc-ba4a-a63892f96a25",
            "entity_def_id": "organization",
            "value": "Grayshift"
          },
          {
            "permalink": "metrc",
            "image_id": "fhjpsad18crkbgtpz6wh",
            "uuid": "e8fcf11e-8878-4c46-8e66-f4544259fdce",
            "entity_def_id": "organization",
            "value": "Metrc"
          },
          {
            "permalink": "colt-defense",
            "image_id": "v1483874339/w78ajxwur1gpoegk2ux5.png",
            "uuid": "e3cef7dd-bd86-267e-9705-3ea52b72c22f",
            "entity_def_id": "organization",
            "value": "Colt"
          },
          {
            "permalink": "forensic-logic",
            "image_id": "uxa0xh00ud7wgyecyzxv",
            "uuid": "8b51355b-fdf1-15e3-d59b-6da878519246",
            "entity_def_id": "organization",
            "value": "Forensic Logic"
          }
        ],
        "org_funding_total": {
          "value_usd": 1057918373,
          "currency": "USD",
          "value": 1057918373
        },
        "org_num_investors": 252
      },
      {
        "org_num": 9865,
        "queries": {
          "person": [
            {
              "field_id": "location_identifiers",
              "operator_id": "includes",
              "values": [
                "f110fca2-1055-99f6-996d-011c198b3928"
              ],
              "type": "predicate"
            },
            {
              "field_id": "rank_person",
              "operator_id": "lte",
              "values": [
                140000
              ],
              "type": "predicate"
            },
            {
              "collection_id": "organization.has_primary_organization.forward",
              "query": [
                {
                  "field_id": "facet_ids",
                  "operator_id": "includes",
                  "values": [
                    "company"
                  ],
                  "type": "predicate"
                },
                {
                  "field_id": "location_identifiers",
                  "operator_id": "includes",
                  "values": [
                    "f110fca2-1055-99f6-996d-011c198b3928"
                  ],
                  "type": "predicate"
                },
                {
                  "field_id": "categories",
                  "operator_id": "includes",
                  "values": [
                    "b9bd65b9-20bf-45cc-207d-b70ac35d5bf4"
                  ],
                  "type": "predicate"
                },
                {
                  "field_id": "operating_status",
                  "operator_id": "eq",
                  "values": [
                    "active"
                  ],
                  "type": "predicate"
                },
                {
                  "field_id": "rank_org",
                  "operator_id": "lte",
                  "values": [
                    440000
                  ],
                  "type": "predicate"
                }
              ],
              "type": "sub_query"
            }
          ],
          "organization": [
            {
              "field_id": "facet_ids",
              "operator_id": "includes",
              "values": [
                "company"
              ],
              "type": "predicate"
            },
            {
              "field_id": "location_identifiers",
              "operator_id": "includes",
              "values": [
                "f110fca2-1055-99f6-996d-011c198b3928"
              ],
              "type": "predicate"
            },
            {
              "field_id": "categories",
              "operator_id": "includes",
              "values": [
                "b9bd65b9-20bf-45cc-207d-b70ac35d5bf4"
              ],
              "type": "predicate"
            },
            {
              "field_id": "operating_status",
              "operator_id": "eq",
              "values": [
                "active"
              ],
              "type": "predicate"
            },
            {
              "field_id": "rank_org",
              "operator_id": "lte",
              "values": [
                440000
              ],
              "type": "predicate"
            }
          ],
          "event": [
            {
              "field_id": "location_identifiers",
              "operator_id": "includes",
              "values": [
                "f110fca2-1055-99f6-996d-011c198b3928"
              ],
              "type": "predicate"
            },
            {
              "field_id": "categories",
              "operator_id": "includes",
              "values": [
                "b9bd65b9-20bf-45cc-207d-b70ac35d5bf4"
              ],
              "type": "predicate"
            },
            {
              "collection_id": "principal.has_event.forward",
              "query": [
                {
                  "field_id": "facet_ids",
                  "operator_id": "includes",
                  "values": [
                    "company"
                  ],
                  "type": "predicate"
                },
                {
                  "field_id": "operating_status",
                  "operator_id": "eq",
                  "values": [
                    "active"
                  ],
                  "type": "predicate"
                }
              ],
              "type": "sub_query"
            }
          ]
        },
        "identifier": {
          "permalink": "united-states-consulting-companies",
          "image_id": "v1496166587/lskazpd63pgh1yem1fr1.png",
          "uuid": "1dbb8c75-377e-4101-92c3-2c0a8304a090",
          "entity_def_id": "hub",
          "value": "United States Consulting Companies (Top 10K)"
        },
        "org_identifiers": [
          {
            "permalink": "andela",
            "image_id": "v1496166587/lskazpd63pgh1yem1fr1.png",
            "uuid": "db370339-02d3-ceba-6515-f6357697a7be",
            "entity_def_id": "organization",
            "value": "Andela"
          },
          {
            "permalink": "talkspace",
            "image_id": "kgtqc7khcl8bhpj5i6kq",
            "uuid": "0cf8891f-7afb-1494-7d6c-3a1589074c5e",
            "entity_def_id": "organization",
            "value": "Talkspace"
          },
          {
            "permalink": "cushman-wakefield",
            "image_id": "v1412687385/odz5lueogqcxbuhzskcb.jpg",
            "uuid": "f778d9dd-0b69-1b63-072a-13fc20c5c84f",
            "entity_def_id": "organization",
            "value": "Cushman & Wakefield"
          },
          {
            "permalink": "legalzoom-com",
            "image_id": "v1397207178/d596b0f381fe5eb8d64180274376f8b3.jpg",
            "uuid": "a432107b-13c0-64f4-acff-1a48c7b1fb45",
            "entity_def_id": "organization",
            "value": "LegalZoom"
          },
          {
            "permalink": "on-deck-a441",
            "image_id": "xf83gwfkqosjes5nz0up",
            "uuid": "2f0b630c-e5be-46f0-953f-1cf4c2c1a441",
            "entity_def_id": "organization",
            "value": "On Deck"
          },
          {
            "permalink": "fractal-analytics",
            "image_id": "kruoor8femg9ovhkkcjl",
            "uuid": "98965195-5b95-1c0d-9f66-ea25b60365ba",
            "entity_def_id": "organization",
            "value": "Fractal Analytics"
          },
          {
            "permalink": "ceridian",
            "image_id": "re8dcjamiepioshqsix5",
            "uuid": "312473cc-c2ee-a6f4-6b5a-b405feff2cf0",
            "entity_def_id": "organization",
            "value": "Ceridian"
          },
          {
            "permalink": "booz-allen-hamilton",
            "image_id": "v1415386048/l4q156nrca4k80hffpol.png",
            "uuid": "f03d3087-728a-2811-7fe0-69cab3e7bda8",
            "entity_def_id": "organization",
            "value": "Booz Allen Hamilton"
          }
        ],
        "org_funding_total": {
          "value_usd": 23508625404,
          "currency": "USD",
          "value": 23508625404
        },
        "org_num_investors": 2220
      },
      {
        "org_num": 633,
        "queries": {
          "person": [
            {
              "field_id": "location_identifiers",
              "operator_id": "includes",
              "values": [
                "0501bdfb-4cc1-f757-13ee-889df4919926"
              ],
              "type": "predicate"
            },
            {
              "collection_id": "organization.has_primary_organization.forward",
              "query": [
                {
                  "field_id": "facet_ids",
                  "operator_id": "includes",
                  "values": [
                    "company"
                  ],
                  "type": "predicate"
                },
                {
                  "field_id": "location_identifiers",
                  "operator_id": "includes",
                  "values": [
                    "0501bdfb-4cc1-f757-13ee-889df4919926"
                  ],
                  "type": "predicate"
                },
                {
                  "field_id": "ipo_status",
                  "operator_id": "includes",
                  "values": [
                    "private"
                  ],
                  "type": "predicate"
                },
                {
                  "field_id": "operating_status",
                  "operator_id": "eq",
                  "values": [
                    "active"
                  ],
                  "type": "predicate"
                }
              ],
              "type": "sub_query"
            }
          ],
          "organization": [
            {
              "field_id": "facet_ids",
              "operator_id": "includes",
              "values": [
                "company"
              ],
              "type": "predicate"
            },
            {
              "field_id": "location_identifiers",
              "operator_id": "includes",
              "values": [
                "0501bdfb-4cc1-f757-13ee-889df4919926"
              ],
              "type": "predicate"
            },
            {
              "field_id": "ipo_status",
              "operator_id": "includes",
              "values": [
                "private"
              ],
              "type": "predicate"
            },
            {
              "field_id": "operating_status",
              "operator_id": "eq",
              "values": [
                "active"
              ],
              "type": "predicate"
            }
          ],
          "event": [
            {
              "field_id": "location_identifiers",
              "operator_id": "includes",
              "values": [
                "0501bdfb-4cc1-f757-13ee-889df4919926"
              ],
              "type": "predicate"
            },
            {
              "collection_id": "principal.has_event.forward",
              "query": [
                {
                  "field_id": "facet_ids",
                  "operator_id": "includes",
                  "values": [
                    "company"
                  ],
                  "type": "predicate"
                },
                {
                  "field_id": "ipo_status",
                  "operator_id": "includes",
                  "values": [
                    "private"
                  ],
                  "type": "predicate"
                },
                {
                  "field_id": "operating_status",
                  "operator_id": "eq",
                  "values": [
                    "active"
                  ],
                  "type": "predicate"
                }
              ],
              "type": "sub_query"
            }
          ]
        },
        "identifier": {
          "permalink": "private-west-virginia-companies",
          "image_id": "rr056dudlw4vwlinbrgh",
          "uuid": "8d8f4367-f6d1-4003-8753-50f8a85ed8d1",
          "entity_def_id": "hub",
          "value": "Private West Virginia Companies"
        },
        "org_identifiers": [
          {
            "permalink": "dignifihealth",
            "image_id": "rr056dudlw4vwlinbrgh",
            "uuid": "66e74f1a-bebb-4e8b-872c-0e1d2ceccfd0",
            "entity_def_id": "organization",
            "value": "DignifiHealth"
          },
          {
            "permalink": "core10",
            "image_id": "v1505662036/nnimztbgd7jabp0c4vjl.png",
            "uuid": "abbbb019-1f7e-6e39-1e2d-0a96ee118267",
            "entity_def_id": "organization",
            "value": "Core10"
          },
          {
            "permalink": "apex-towers",
            "image_id": "ipnncz0gwv3o4g6g1tak",
            "uuid": "090372b2-c5be-4ffc-86ac-d803ed5677f1",
            "entity_def_id": "organization",
            "value": "Apex Towers"
          },
          {
            "permalink": "vocinity",
            "image_id": "avanvhoiqaesxw4bhsug",
            "uuid": "c042ddec-d7da-4164-a4a5-089c66a489a7",
            "entity_def_id": "organization",
            "value": "Vocinity"
          },
          {
            "permalink": "swilled-dog",
            "image_id": "tnvfnb2zt0guju6s5olv",
            "uuid": "9d66c6ad-f42b-4764-a82a-a8c0ac90581e",
            "entity_def_id": "organization",
            "value": "Swilled Dog"
          },
          {
            "permalink": "realx-ventures",
            "image_id": "xyuer7jknxovfcp6gby3",
            "uuid": "b34834f4-0ca5-4b91-b6e1-fd0fa0d6cb96",
            "entity_def_id": "organization",
            "value": "RealX Ventures"
          },
          {
            "permalink": "eastern-vault",
            "image_id": "fkqgm6akqfvyt8k5quj4",
            "uuid": "ce02faf2-d5cd-46b7-b53b-b32f81009877",
            "entity_def_id": "organization",
            "value": "Eastern Vault"
          },
          {
            "permalink": "fairmont-brine-processing",
            "image_id": "v1461044613/dtvthegqss6sngwpx298.png",
            "uuid": "a44959f0-b270-79d1-6761-f3b1e991e9ef",
            "entity_def_id": "organization",
            "value": "Fairmont Brine Processing"
          }
        ],
        "org_funding_total": {
          "value_usd": 149895364,
          "currency": "USD",
          "value": 149895364
        },
        "org_num_investors": 32
      },
      {
        "org_num": 9907,
        "queries": {
          "person": [
            {
              "field_id": "rank_person",
              "operator_id": "lte",
              "values": [
                190000
              ],
              "type": "predicate"
            },
            {
              "collection_id": "organization.has_primary_organization.forward",
              "query": [
                {
                  "field_id": "facet_ids",
                  "operator_id": "includes",
                  "values": [
                    "company"
                  ],
                  "type": "predicate"
                },
                {
                  "field_id": "categories",
                  "operator_id": "includes",
                  "values": [
                    "b1234a83-0ad1-c131-b788-81f8eb48c35e"
                  ],
                  "type": "predicate"
                },
                {
                  "field_id": "operating_status",
                  "operator_id": "eq",
                  "values": [
                    "active"
                  ],
                  "type": "predicate"
                },
                {
                  "field_id": "rank_org",
                  "operator_id": "lte",
                  "values": [
                    960000
                  ],
                  "type": "predicate"
                }
              ],
              "type": "sub_query"
            }
          ],
          "organization": [
            {
              "field_id": "facet_ids",
              "operator_id": "includes",
              "values": [
                "company"
              ],
              "type": "predicate"
            },
            {
              "field_id": "categories",
              "operator_id": "includes",
              "values": [
                "b1234a83-0ad1-c131-b788-81f8eb48c35e"
              ],
              "type": "predicate"
            },
            {
              "field_id": "operating_status",
              "operator_id": "eq",
              "values": [
                "active"
              ],
              "type": "predicate"
            },
            {
              "field_id": "rank_org",
              "operator_id": "lte",
              "values": [
                960000
              ],
              "type": "predicate"
            }
          ],
          "event": [
            {
              "field_id": "categories",
              "operator_id": "includes",
              "values": [
                "b1234a83-0ad1-c131-b788-81f8eb48c35e"
              ],
              "type": "predicate"
            },
            {
              "collection_id": "principal.has_event.forward",
              "query": [
                {
                  "field_id": "facet_ids",
                  "operator_id": "includes",
                  "values": [
                    "company"
                  ],
                  "type": "predicate"
                },
                {
                  "field_id": "operating_status",
                  "operator_id": "eq",
                  "values": [
                    "active"
                  ],
                  "type": "predicate"
                }
              ],
              "type": "sub_query"
            }
          ]
        },
        "identifier": {
          "permalink": "legal-companies",
          "image_id": "oabtfnipqfox2setpz8m",
          "uuid": "a8f798ab-da7f-44e2-9b22-62059ac14684",
          "entity_def_id": "hub",
          "value": "Legal Companies (Top 10K)"
        },
        "org_identifiers": [
          {
            "permalink": "clio",
            "image_id": "oabtfnipqfox2setpz8m",
            "uuid": "5d9400d9-0e32-3274-1bda-a8168cc14e65",
            "entity_def_id": "organization",
            "value": "Clio"
          },
          {
            "permalink": "transunion",
            "image_id": "sljogfbctrnfgtyqdlld",
            "uuid": "31de49d9-4081-2c13-2a4b-e0b6a160d783",
            "entity_def_id": "organization",
            "value": "TransUnion"
          },
          {
            "permalink": "ironclad",
            "image_id": "jqeacbadxfgjkjctehtb",
            "uuid": "27bde34d-e097-a59b-fa3b-0a8b7bc1d510",
            "entity_def_id": "organization",
            "value": "Ironclad"
          },
          {
            "permalink": "notarize",
            "image_id": "xf3ijv88eqme4m7lpfbj",
            "uuid": "225c0cb7-084d-4cc2-6f3c-d34f92507ad2",
            "entity_def_id": "organization",
            "value": "Notarize"
          },
          {
            "permalink": "rocketlawyer",
            "image_id": "v1399569442/bvwlhoswhk9hysd5iwwm.png",
            "uuid": "bb63e3a5-4c75-6219-5d7f-f9d492cfcc6f",
            "entity_def_id": "organization",
            "value": "Rocket Lawyer"
          },
          {
            "permalink": "checkr",
            "image_id": "xzmghoxtzgtu3hbrn8r8",
            "uuid": "ffe232c5-fcf4-e08e-b43d-c7dd1d5fc32c",
            "entity_def_id": "organization",
            "value": "Checkr"
          },
          {
            "permalink": "cushman-wakefield",
            "image_id": "v1412687385/odz5lueogqcxbuhzskcb.jpg",
            "uuid": "f778d9dd-0b69-1b63-072a-13fc20c5c84f",
            "entity_def_id": "organization",
            "value": "Cushman & Wakefield"
          },
          {
            "permalink": "legalzoom-com",
            "image_id": "v1397207178/d596b0f381fe5eb8d64180274376f8b3.jpg",
            "uuid": "a432107b-13c0-64f4-acff-1a48c7b1fb45",
            "entity_def_id": "organization",
            "value": "LegalZoom"
          }
        ],
        "org_funding_total": {
          "value_usd": 12639256214,
          "currency": "USD",
          "value": 12639256214
        },
        "org_num_investors": 2428
      }
    ],
    "investors_summary": {
      "identifier": {
        "uuid": "659eff91-c557-46a9-8655-66289b4ab451",
        "value": "Warner",
        "image_id": "wmlnt4ssvplwk2snjlvg",
        "permalink": "warner-law-offices",
        "entity_def_id": "organization"
      }
    },
    "funds_list": [],
    "key_employee_change_list": [
      {
        "identifier": {
          "uuid": "38743ed4-e39d-410c-90c1-e85feed38c85",
          "entity_def_id": "key_employee_change"
        },
        "key_event_date": "2021-03-01",
        "press_reference_link": {
          "label": "Crowley Maritime Corp. Promotes Dan Warner to Chief Financial Officer",
          "value": "https://www.prweb.com/releases/crowley_maritime_corp_promotes_dan_warner_to_chief_financial_officer/prweb17760268.htm"
        }
      }
    ],
    "alumni_image_list": [],
    "exits_summary": {
      "identifier": {
        "uuid": "659eff91-c557-46a9-8655-66289b4ab451",
        "value": "Warner",
        "image_id": "wmlnt4ssvplwk2snjlvg",
        "permalink": "warner-law-offices",
        "entity_def_id": "organization"
      }
    },
    "bombora_surge_list": [
      {
        "uuid": "78438cc8-2d25-447f-ae77-81c2bb7ff83e",
        "topic_identifier": {
          "uuid": "79e2715c-2ba9-433e-9e96-1d7b13b8362b",
          "value": "Economy",
          "entity_def_id": "bombora_topic"
        },
        "surge_score": 88,
        "identifier": {
          "uuid": "78438cc8-2d25-447f-ae77-81c2bb7ff83e"
        }
      },
      {
        "uuid": "f5956a95-944c-41ab-b2c3-9868d2ccc328",
        "topic_identifier": {
          "uuid": "1964edd1-587f-466c-bdf2-4e5be9f7428c",
          "value": "Conflict Resolution",
          "entity_def_id": "bombora_topic"
        },
        "surge_score": 80,
        "identifier": {
          "uuid": "f5956a95-944c-41ab-b2c3-9868d2ccc328"
        }
      },
      {
        "uuid": "29cc6a97-b4d7-4d1b-83d4-7fd54b2021dd",
        "topic_identifier": {
          "uuid": "e6695b36-6f2c-454b-8690-9d2b917d0bdc",
          "value": "Research and Development / Test",
          "entity_def_id": "bombora_topic"
        },
        "surge_score": 66,
        "identifier": {
          "uuid": "29cc6a97-b4d7-4d1b-83d4-7fd54b2021dd"
        }
      }
    ],
    "diversity_spotlight_investments_list": [],
    "builtwith_tech_used_list": [],
    "funding_rounds_summary": {
      "identifier": {
        "uuid": "659eff91-c557-46a9-8655-66289b4ab451",
        "value": "Warner",
        "image_id": "wmlnt4ssvplwk2snjlvg",
        "permalink": "warner-law-offices",
        "entity_def_id": "organization"
      }
    },
    "acquisitions_summary": {
      "identifier": {
        "uuid": "659eff91-c557-46a9-8655-66289b4ab451",
        "value": "Warner",
        "image_id": "wmlnt4ssvplwk2snjlvg",
        "permalink": "warner-law-offices",
        "entity_def_id": "organization"
      }
    },
    "advisors_summary": {
      "identifier": {
        "uuid": "659eff91-c557-46a9-8655-66289b4ab451",
        "value": "Warner",
        "image_id": "wmlnt4ssvplwk2snjlvg",
        "permalink": "warner-law-offices",
        "entity_def_id": "organization"
      }
    },
    "acquisitions_list": [],
    "alumni_headline": {},
    "exits_headline": {},
    "investments_summary": {
      "identifier": {
        "uuid": "659eff91-c557-46a9-8655-66289b4ab451",
        "value": "Warner",
        "image_id": "wmlnt4ssvplwk2snjlvg",
        "permalink": "warner-law-offices",
        "entity_def_id": "organization"
      }
    },
    "acquired_by_fields": {},
    "sub_organizations_headline": {},
    "layoff_list": [],
    "overview_school_fields": {},
    "bombora_summary": {
      "identifier": {
        "uuid": "659eff91-c557-46a9-8655-66289b4ab451",
        "value": "Warner",
        "image_id": "wmlnt4ssvplwk2snjlvg",
        "permalink": "warner-law-offices",
        "entity_def_id": "organization"
      }
    },
    "semrush_rank_headline": {},
    "alumni_summary": {
      "identifier": {
        "uuid": "659eff91-c557-46a9-8655-66289b4ab451",
        "value": "Warner",
        "image_id": "wmlnt4ssvplwk2snjlvg",
        "permalink": "warner-law-offices",
        "entity_def_id": "organization"
      }
    },
    "apptopia_summary": {
      "identifier": {
        "uuid": "659eff91-c557-46a9-8655-66289b4ab451",
        "value": "Warner",
        "image_id": "wmlnt4ssvplwk2snjlvg",
        "permalink": "warner-law-offices",
        "entity_def_id": "organization"
      }
    },
    "diversity_spotlight_investments_summary": {
      "identifier": {
        "uuid": "659eff91-c557-46a9-8655-66289b4ab451",
        "value": "Warner",
        "image_id": "wmlnt4ssvplwk2snjlvg",
        "permalink": "warner-law-offices",
        "entity_def_id": "organization"
      }
    },
    "contact_fields": {
      "contact_email": "tbartlett@wvpersonalinjury.com",
      "phone_number": "+1 304-345-6789"
    },
    "social_fields": {
      "facebook": {
        "value": "https://www.facebook.com/WarnerLawOffices"
      },
      "linkedin": {
        "value": "https://www.linkedin.com/company/warnerlawoffices/"
      },
      "twitter": {
        "value": "https://twitter.com/WarnerLawWV"
      }
    },
    "investments_headline": {},
    "sub_organizations_summary": {
      "identifier": {
        "uuid": "659eff91-c557-46a9-8655-66289b4ab451",
        "value": "Warner",
        "image_id": "wmlnt4ssvplwk2snjlvg",
        "permalink": "warner-law-offices",
        "entity_def_id": "organization"
      }
    },
    "overview_description": {},
    "current_employees_featured_order_field": [],
    "company_about_fields2": {
      "website": {
        "value": "https://www.wvpersonalinjury.com/"
      },
      "ipo_status": "private",
      "num_employees_enum": "c_00011_00050",
      "location_identifiers": [
        {
          "uuid": "d72bc56e-aa74-52af-4873-3f90b3d88ff8",
          "value": "Charleston",
          "permalink": "charleston-west-virginia",
          "entity_def_id": "location",
          "location_type": "city"
        },
        {
          "uuid": "0501bdfb-4cc1-f757-13ee-889df4919926",
          "value": "West Virginia",
          "permalink": "west-virginia-united-states",
          "entity_def_id": "location",
          "location_type": "region"
        },
        {
          "uuid": "f110fca2-1055-99f6-996d-011c198b3928",
          "value": "United States",
          "permalink": "united-states",
          "entity_def_id": "location",
          "location_type": "country"
        },
        {
          "uuid": "b25caef9-a1b8-3a5d-6232-93b2dfb6a1d1",
          "value": "North America",
          "permalink": "north-america",
          "entity_def_id": "location",
          "location_type": "continent"
        }
      ],
      "rank_org_company": 220393
    },
    "sub_organizations_image_list": [],
    "investors_headline": {},
    "ipo_summary": {
      "identifier": {
        "uuid": "659eff91-c557-46a9-8655-66289b4ab451",
        "value": "Warner",
        "image_id": "wmlnt4ssvplwk2snjlvg",
        "permalink": "warner-law-offices",
        "entity_def_id": "organization"
      }
    },
    "ipqwery_summary": {
      "identifier": {
        "uuid": "659eff91-c557-46a9-8655-66289b4ab451",
        "value": "Warner",
        "image_id": "wmlnt4ssvplwk2snjlvg",
        "permalink": "warner-law-offices",
        "entity_def_id": "organization"
      }
    },
    "siftery_product_list": [],
    "overview_fields_extended": {
      "categories": [
        {
          "uuid": "b9bd65b9-20bf-45cc-207d-b70ac35d5bf4",
          "value": "Consulting",
          "permalink": "consulting",
          "entity_def_id": "category"
        },
        {
          "uuid": "98de1ee2-4c3b-be26-0f7b-46fddbbfe76d",
          "value": "Law Enforcement",
          "permalink": "law-enforcement",
          "entity_def_id": "category"
        },
        {
          "uuid": "b1234a83-0ad1-c131-b788-81f8eb48c35e",
          "value": "Legal",
          "permalink": "legal",
          "entity_def_id": "category"
        }
      ],
      "founded_on": {
        "value": "2006-01-01",
        "precision": "year"
      },
      "location_group_identifiers": [
        {
          "uuid": "090db99d-13e7-455a-a0e4-95cd21211c92",
          "value": "Southern US",
          "permalink": "southern-united-states",
          "entity_def_id": "location",
          "location_type": "group"
        }
      ],
      "operating_status": "active"
    },
    "semrush_location_list": [],
    "overview_investor_fields": {},
    "investors_list": [],
    "siftery_summary": {
      "identifier": {
        "uuid": "659eff91-c557-46a9-8655-66289b4ab451",
        "value": "Warner",
        "image_id": "wmlnt4ssvplwk2snjlvg",
        "permalink": "warner-law-offices",
        "entity_def_id": "organization"
      }
    },
    "acquired_by_summary": {
      "identifier": {
        "uuid": "659eff91-c557-46a9-8655-66289b4ab451",
        "value": "Warner",
        "image_id": "wmlnt4ssvplwk2snjlvg",
        "permalink": "warner-law-offices",
        "entity_def_id": "organization"
      }
    },
    "ipo_fields": {},
    "apptopia_app_overview_list_public": [],
    "trading_view": {},
    "news_headline": {
      "num_articles": 20
    },
    "current_employees_image_list": [],
    "privco_summary_public": {
      "identifier": {
        "uuid": "659eff91-c557-46a9-8655-66289b4ab451",
        "value": "Warner",
        "image_id": "wmlnt4ssvplwk2snjlvg",
        "permalink": "warner-law-offices",
        "entity_def_id": "organization"
      }
    },
    "event_appearances_summary": {
      "identifier": {
        "uuid": "659eff91-c557-46a9-8655-66289b4ab451",
        "value": "Warner",
        "image_id": "wmlnt4ssvplwk2snjlvg",
        "permalink": "warner-law-offices",
        "entity_def_id": "organization"
      }
    },
    "diversity_spotlight_investments_headline": {},
    "funding_rounds_list": [],
    "technology_highlights": {
      "builtwith_num_technologies_used": 24
    },
    "funding_rounds_headline": {},
    "investments_list": [],
    "exits_image_list": [],
    "funds_headline": {},
    "people_highlights": {},
    "current_employees_headline": {},
    "semrush_attribution": {},
    "event_appearances_list": [],
    "current_employees_summary": {
      "identifier": {
        "uuid": "659eff91-c557-46a9-8655-66289b4ab451",
        "value": "Warner",
        "image_id": "wmlnt4ssvplwk2snjlvg",
        "permalink": "warner-law-offices",
        "entity_def_id": "organization"
      }
    },
    "funds_summary": {
      "identifier": {
        "uuid": "659eff91-c557-46a9-8655-66289b4ab451",
        "value": "Warner",
        "image_id": "wmlnt4ssvplwk2snjlvg",
        "permalink": "warner-law-offices",
        "entity_def_id": "organization"
      }
    },
    "aberdeen_summary": {
      "aberdeen_site_it_spend": {
        "value": 37047,
        "currency": "USD",
        "value_usd": 37047
      },
      "identifier": {
        "uuid": "659eff91-c557-46a9-8655-66289b4ab451",
        "value": "Warner",
        "image_id": "wmlnt4ssvplwk2snjlvg",
        "permalink": "warner-law-offices",
        "entity_def_id": "organization"
      }
    },
    "company_financials_highlights": {},
    "overview_company_fields": {
      "company_type": "for_profit"
    },
    "acquisitions_headline": {},
    "builtwith_summary": {
      "builtwith_num_technologies_used": 24,
      "identifier": {
        "uuid": "659eff91-c557-46a9-8655-66289b4ab451",
        "value": "Warner",
        "image_id": "wmlnt4ssvplwk2snjlvg",
        "permalink": "warner-law-offices",
        "entity_def_id": "organization"
      }
    },
    "advisors_headline": {},
    "about_short_description": {
      "short_description": "Warner is a personal injury firm that offers miners, loggers, construction and other workers in personal injury & wrongful death litigation."
    },
    "event_appearances_headline": {},
    "apptopia_app_headline": {},
    "company_overview_highlights": {}
  }
}
```

### Event
```json
{
  "properties": {
    "short_description": "Join us for a fireside chat with Andrew Warner the Founder of Bot Academy & Mixergy.",
    "facet_ids": [
      "rank"
    ],
    "identifier": {
      "uuid": "6533e7b7-5c72-fdb1-7979-dbace11b1f09",
      "value": "Messenger Chatbots- The Secret to 8X Engagement",
      "image_id": "v1507051038/plgndkbsyrjdinydhgf1.png",
      "permalink": "messenger-chatbots-the-secret-to-8x-engagement-20171010",
      "entity_def_id": "event"
    },
    "title": "Messenger Chatbots- The Secret to 8X Engagement - 2017-10-10"
  },
  "cards": {
    "sponsors_headline": {},
    "sponsors_summary": {
      "identifier": {
        "uuid": "6533e7b7-5c72-fdb1-7979-dbace11b1f09",
        "value": "Messenger Chatbots- The Secret to 8X Engagement",
        "image_id": "v1507051038/plgndkbsyrjdinydhgf1.png",
        "permalink": "messenger-chatbots-the-secret-to-8x-engagement-20171010",
        "entity_def_id": "event"
      }
    },
    "sponsors_image_list": [],
    "speakers_image_list": [
      {
        "identifier": {
          "uuid": "a4e7ddf7-42eb-1e49-6d3e-6cef4fd065b5",
          "value": "Andrew Warner",
          "image_id": "v1472468098/qtlazysvloy6vrfvluvz.png",
          "permalink": "andrew-warner",
          "entity_def_id": "person"
        },
        "primary_job_title": "Founder",
        "primary_organization": {
          "uuid": "310715db-3aaf-a011-c380-c1791f20b845",
          "value": "Mixergy",
          "image_id": "v1410281195/xjbccxlruobyuabbeiyu.jpg",
          "permalink": "mixergy",
          "entity_def_id": "organization"
        }
      }
    ],
    "overview_fields_v2": {
      "location_group_identifiers": [
        {
          "uuid": "f79bcf34-5d9e-4a01-837e-f6012edd056c",
          "value": "San Francisco Bay Area",
          "permalink": "san-francisco-bay-area-california",
          "entity_def_id": "location",
          "location_type": "group"
        },
        {
          "uuid": "cf97b169-46c9-493f-a20f-3fe590824934",
          "value": "West Coast",
          "permalink": "west-coast-united-states",
          "entity_def_id": "location",
          "location_type": "group"
        },
        {
          "uuid": "f37257c7-3745-42a1-8e07-b7db80a362ac",
          "value": "Western US",
          "permalink": "western-united-states",
          "entity_def_id": "location",
          "location_type": "group"
        }
      ],
      "ends_on": "2017-10-10",
      "short_description": "Join us for a fireside chat with Andrew Warner the Founder of Bot Academy & Mixergy.",
      "venue_name": "Will be released after registration",
      "registration_url": {
        "value": "https://www.eventbrite.com/e/messenger-chatbots-the-secret-to-8x-engagement-tickets-37991300001?utm_source=eb_email&utm_medium=email&utm_campaign=order_confirmation_email&utm_term=eventname&ref=eemailordconf"
      },
      "event_type": [
        "other"
      ],
      "location_identifiers": [
        {
          "uuid": "528f5e3c-90d1-1111-5d1c-2e4ff979d58e",
          "value": "San Francisco",
          "permalink": "san-francisco-california",
          "entity_def_id": "location",
          "location_type": "city"
        },
        {
          "uuid": "eb879a83-c91a-121e-0bb8-829782dbcf04",
          "value": "California",
          "permalink": "california-united-states",
          "entity_def_id": "location",
          "location_type": "region"
        },
        {
          "uuid": "f110fca2-1055-99f6-996d-011c198b3928",
          "value": "United States",
          "permalink": "united-states",
          "entity_def_id": "location",
          "location_type": "country"
        },
        {
          "uuid": "b25caef9-a1b8-3a5d-6232-93b2dfb6a1d1",
          "value": "North America",
          "permalink": "north-america",
          "entity_def_id": "location",
          "location_type": "continent"
        }
      ],
      "starts_on": "2017-10-10"
    },
    "speakers_headline": {
      "num_speakers": 1
    },
    "contestants_summary": {
      "identifier": {
        "uuid": "6533e7b7-5c72-fdb1-7979-dbace11b1f09",
        "value": "Messenger Chatbots- The Secret to 8X Engagement",
        "image_id": "v1507051038/plgndkbsyrjdinydhgf1.png",
        "permalink": "messenger-chatbots-the-secret-to-8x-engagement-20171010",
        "entity_def_id": "event"
      }
    },
    "overview_description": {},
    "exhibitors_headline": {},
    "contestants_headline": {},
    "overview_headline": {
      "num_speakers": 1
    },
    "speakers_summary": {
      "identifier": {
        "uuid": "6533e7b7-5c72-fdb1-7979-dbace11b1f09",
        "value": "Messenger Chatbots- The Secret to 8X Engagement",
        "image_id": "v1507051038/plgndkbsyrjdinydhgf1.png",
        "permalink": "messenger-chatbots-the-secret-to-8x-engagement-20171010",
        "entity_def_id": "event"
      },
      "num_speakers": 1
    },
    "contestants_image_list": [],
    "exhibitors_summary": {
      "identifier": {
        "uuid": "6533e7b7-5c72-fdb1-7979-dbace11b1f09",
        "value": "Messenger Chatbots- The Secret to 8X Engagement",
        "image_id": "v1507051038/plgndkbsyrjdinydhgf1.png",
        "permalink": "messenger-chatbots-the-secret-to-8x-engagement-20171010",
        "entity_def_id": "event"
      }
    },
    "hubs_list": [],
    "exhibitors_image_list": []
  }
}
```

### Hub
```json
{
  "properties": {
    "short_description": "Companies and startups in European Union (EU) in the saas space.",
    "facet_ids": [
      "rank"
    ],
    "title": "List of top European Union (EU) SaaS Companies",
    "identifier": {
      "uuid": "3c9b22a5-aac2-4699-9974-488423546fb1",
      "value": "European Union (EU) SaaS Companies",
      "image_id": "uoi3fphr5wqsrfxnastp",
      "permalink": "european-union-saas-companies",
      "entity_def_id": "hub"
    }
  },
  "cards": {
    "overview_org_stat_fields": {
      "org_percent_acquired": 0.0826219512195122,
      "org_founded_on_avg": "2013-06-04",
      "org_num_founders": 4625,
      "org_num_company_non_profit": 2,
      "org_num_company_for_profit": 3214,
      "org_percent_public": 0.00426829268292683,
      "org_top_funding_types": [
        "seed",
        "series_a",
        "series_unknown",
        "pre_seed",
        "angel"
      ],
      "org_top_investor_types": [
        "venture_capital",
        "corporate_venture_capital",
        "incubator",
        "micro_vc",
        "accelerator"
      ],
      "org_percent_non_profit": 0.0006097560975609756
    },
    "org_top_rank_delta_d30_list": [
      {
        "rank_delta_d30": 9.9,
        "identifier": {
          "permalink": "glambook",
          "image_id": "nxnnjkfn0pqd7dwfdyms",
          "uuid": "ddf13867-8eba-4d0c-9e0e-453b68010d99",
          "entity_def_id": "organization",
          "value": "Glambook"
        },
        "rank_org": 20064,
        "funding_total": {
          "value_usd": 608162,
          "currency": "EUR",
          "value": 500000
        }
      },
      {
        "rank_delta_d30": 9.9,
        "identifier": {
          "permalink": "digitoo",
          "image_id": "ysvk7ar0p0zyxypqarf8",
          "uuid": "b5a9b5c0-cf69-4ef5-8350-f9ef26b7f12f",
          "entity_def_id": "organization",
          "value": "Digitoo"
        },
        "rank_org": 25830,
        "funding_total": {
          "value_usd": 1518027,
          "currency": "EUR",
          "value": 1250000
        }
      },
      {
        "rank_delta_d30": 9.8,
        "identifier": {
          "permalink": "semana-a81f",
          "image_id": "n17tcqqkeyeim0c9ca7o",
          "uuid": "32503a6f-464e-4482-8b46-bef1241ea81f",
          "entity_def_id": "organization",
          "value": "Semana"
        },
        "rank_org": 34156,
        "funding_total": {
          "value_usd": 723918,
          "currency": "EUR",
          "value": 600000
        }
      },
      {
        "rank_delta_d30": 9.8,
        "identifier": {
          "permalink": "replay-institute",
          "image_id": "orgqk6rpdhulcjqhcxwc",
          "uuid": "acec41b0-9f30-408e-88b0-3ae7b0e5ef28",
          "entity_def_id": "organization",
          "value": "Replay Institute"
        },
        "rank_org": 34905,
        "funding_total": {
          "value_usd": 727797,
          "currency": "DKK",
          "value": 4500000
        }
      },
      {
        "rank_delta_d30": 9.7,
        "identifier": {
          "permalink": "expensya",
          "image_id": "y6dju6dbtau9ryy6bzde",
          "uuid": "030dccf1-cc61-d5f4-5aab-4a161a609e07",
          "entity_def_id": "organization",
          "value": "Expensya"
        },
        "rank_org": 923,
        "funding_total": {
          "value_usd": 25600000,
          "currency": "USD",
          "value": 25600000
        }
      }
    ],
    "person_headline": {
      "person_num": 996
    },
    "org_funding_headline": {
      "org_funding_total": {
        "value": 12042483377,
        "currency": "USD",
        "value_usd": 12042483377
      },
      "org_num_funding_rounds": 3473,
      "org_num_funding_rounds_median": 2
    },
    "org_top_rank_delta_d30_headline": {
      "org_num": 3280,
      "org_rank_avg": 278011.7637195122
    },
    "org_ipos_fields": {
      "org_ipo_valuation_total": {
        "value": 440570211,
        "currency": "USD",
        "value_usd": 440570211
      },
      "org_went_public_on_avg": "2012-07-03",
      "org_ipo_valuation_median": {
        "value": 23411585,
        "currency": "USD",
        "value_usd": 23411585
      },
      "org_ipo_amount_raised_median": {
        "value": 4209539.5,
        "currency": "USD",
        "value_usd": 4209539.5
      },
      "org_percent_delisted": 0.0003048780487804878
    },
    "org_acquisitions_headline": {
      "org_num_acquisitions": 274
    },
    "principal_investments_list": [
      {
        "identifier": {
          "entity_def_id": "investment",
          "permalink": "point-nine-capital-invested-in-pento-series-a--fcf36d25--81a91697",
          "uuid": "81a91697-1b3c-44e3-b08e-180cec658854",
          "value": "Point Nine investment in Series A - Pento"
        },
        "announced_on": "2021-05-19",
        "funding_round_identifier": {
          "permalink": "pento-series-a--fcf36d25",
          "image_id": "ek1htap8cbmcq5szpipe",
          "uuid": "fcf36d25-d522-404d-9a48-05f155730059",
          "entity_def_id": "funding_round",
          "value": "Series A - Pento"
        },
        "funding_round_money_raised": {
          "value_usd": 15492603,
          "currency": "EUR",
          "value": 12700000
        },
        "investor_identifier": {
          "permalink": "point-nine-capital",
          "image_id": "ckicqpmuamymvmjcdz2x",
          "uuid": "e8de4e94-b48c-76f6-3770-aac7e51158f4",
          "entity_def_id": "organization",
          "value": "Point Nine"
        }
      },
      {
        "identifier": {
          "entity_def_id": "investment",
          "permalink": "phillip-chambers-invested-in-payslip-series-a--b68a9574--3f714717",
          "uuid": "3f714717-7fda-44a3-8aa7-3dfef293c90b",
          "value": "Phillip Chambers investment in Series A - Payslip"
        },
        "announced_on": "2021-05-18",
        "funding_round_identifier": {
          "permalink": "payslip-series-a--b68a9574",
          "image_id": "uso3ich8x3i9ubd6w2fv",
          "uuid": "b68a9574-efea-4ffa-aa1b-4480d893f710",
          "entity_def_id": "funding_round",
          "value": "Series A - Payslip"
        },
        "funding_round_money_raised": {
          "value_usd": 10107024,
          "currency": "EUR",
          "value": 8300000
        },
        "investor_identifier": {
          "permalink": "phillip-chambers",
          "image_id": "l6qhwdlplnzdr8aqoxsl",
          "uuid": "2e8ebc91-988a-401b-90e2-0573f18f7371",
          "entity_def_id": "person",
          "value": "Phillip Chambers"
        }
      },
      {
        "identifier": {
          "entity_def_id": "investment",
          "permalink": "anna-rose-invested-in-deversifi-initial-coin-offering--ad380e69--afedde9a",
          "uuid": "afedde9a-6f47-4886-b336-48c25c077b67",
          "value": "Anna Rose investment in Initial Coin Offering - DeversiFi"
        },
        "announced_on": "2021-05-18",
        "funding_round_identifier": {
          "permalink": "deversifi-initial-coin-offering--ad380e69",
          "image_id": "wi3kuwworhdqivdt3fpj",
          "uuid": "ad380e69-cb39-41e7-93ab-a9c54be0dfb1",
          "entity_def_id": "funding_round",
          "value": "Initial Coin Offering - DeversiFi"
        },
        "funding_round_money_raised": {
          "value_usd": 5000000,
          "currency": "USD",
          "value": 5000000
        },
        "investor_identifier": {
          "permalink": "anna-rose",
          "image_id": "v1431001017/pn7rv9iynyn3ztt6wcuz.png",
          "uuid": "b191ed23-3e06-c7dc-afe0-d76f1dc820fe",
          "entity_def_id": "person",
          "value": "Anna Rose"
        }
      },
      {
        "identifier": {
          "entity_def_id": "investment",
          "permalink": "bjorn-kolbmuller-invested-in-vcoach-pre-seed--565fbfe1--efe342d3",
          "uuid": "efe342d3-9843-48a4-9b6e-678fa539491b",
          "value": "Bjorn Kolbmuller investment in Pre Seed Round - vCOACH"
        },
        "announced_on": "2021-05-17",
        "funding_round_identifier": {
          "permalink": "vcoach-pre-seed--565fbfe1",
          "image_id": "kfmuqy40ty87ncegma2e",
          "uuid": "565fbfe1-4cd1-4cb0-aef6-4d0ec766cfed",
          "entity_def_id": "funding_round",
          "value": "Pre Seed Round - vCOACH"
        },
        "investor_identifier": {
          "permalink": "bjorn-kolbmuller",
          "image_id": "ouuzd75ofhvzjgskkg43",
          "uuid": "6fc49a45-2926-1204-a8dc-e158a0d18fe5",
          "entity_def_id": "person",
          "value": "Bjorn Kolbmuller"
        }
      },
      {
        "identifier": {
          "entity_def_id": "investment",
          "permalink": "point-nine-capital-invested-in-metalshub-series-a--41318a58--a1302c7c",
          "uuid": "a1302c7c-c858-456b-8e88-cf7f2177dd11",
          "value": "Point Nine investment in Series A - Metalshub"
        },
        "announced_on": "2021-05-05",
        "funding_round_identifier": {
          "permalink": "metalshub-series-a--41318a58",
          "image_id": "tyg9xkv11la5hio4dwoy",
          "uuid": "41318a58-d266-4eb6-9415-90801cd3dcb8",
          "entity_def_id": "funding_round",
          "value": "Series A - Metalshub"
        },
        "funding_round_money_raised": {
          "value_usd": 11000000,
          "currency": "USD",
          "value": 11000000
        },
        "investor_identifier": {
          "permalink": "point-nine-capital",
          "image_id": "ckicqpmuamymvmjcdz2x",
          "uuid": "e8de4e94-b48c-76f6-3770-aac7e51158f4",
          "entity_def_id": "organization",
          "value": "Point Nine"
        }
      }
    ],
    "event_list": [
      {
        "identifier": {
          "permalink": "saastock19",
          "image_id": "h4yszmtolrr7izjsk1jy",
          "uuid": "281838a2-8256-4341-86e3-413990058d7d",
          "entity_def_id": "event",
          "value": "SaaStock19"
        },
        "location_identifiers": [
          {
            "permalink": "dublin-dublin",
            "uuid": "97c70aa1-7568-ca53-7512-2f181f0484a7",
            "location_type": "city",
            "entity_def_id": "location",
            "value": "Dublin"
          },
          {
            "permalink": "dublin-ireland",
            "uuid": "e401019b-70f7-46ee-f7f3-3331a2528672",
            "location_type": "region",
            "entity_def_id": "location",
            "value": "Dublin"
          },
          {
            "permalink": "ireland",
            "uuid": "1944e9da-82b4-8190-38c0-014fef22e2ef",
            "location_type": "country",
            "entity_def_id": "location",
            "value": "Ireland"
          },
          {
            "permalink": "europe",
            "uuid": "6106f5dc-823e-5da8-40d7-51612c0b2c4e",
            "location_type": "continent",
            "entity_def_id": "location",
            "value": "Europe"
          }
        ],
        "rank_event": 819,
        "starts_on": "2019-10-14"
      },
      {
        "identifier": {
          "permalink": "saastock20-dublin",
          "image_id": "jztk0rd52fhvoesv2ejm",
          "uuid": "197967a8-a59f-4eee-84aa-4ac813f3d3c9",
          "entity_def_id": "event",
          "value": "SaaStock20 | Dublin"
        },
        "location_identifiers": [
          {
            "permalink": "dublin-dublin",
            "uuid": "97c70aa1-7568-ca53-7512-2f181f0484a7",
            "location_type": "city",
            "entity_def_id": "location",
            "value": "Dublin"
          },
          {
            "permalink": "dublin-ireland",
            "uuid": "e401019b-70f7-46ee-f7f3-3331a2528672",
            "location_type": "region",
            "entity_def_id": "location",
            "value": "Dublin"
          },
          {
            "permalink": "ireland",
            "uuid": "1944e9da-82b4-8190-38c0-014fef22e2ef",
            "location_type": "country",
            "entity_def_id": "location",
            "value": "Ireland"
          },
          {
            "permalink": "europe",
            "uuid": "6106f5dc-823e-5da8-40d7-51612c0b2c4e",
            "location_type": "continent",
            "entity_def_id": "location",
            "value": "Europe"
          }
        ],
        "rank_event": 3338,
        "starts_on": "2020-10-12"
      },
      {
        "identifier": {
          "permalink": "saastock-2016-2016122",
          "image_id": "v1453221264/epxfczquaxwripqqbzog.png",
          "uuid": "541b1664-4ec6-042f-8b51-0d9bad2cbdea",
          "entity_def_id": "event",
          "value": "SaaStock 2016"
        },
        "location_identifiers": [
          {
            "permalink": "dublin-dublin",
            "uuid": "97c70aa1-7568-ca53-7512-2f181f0484a7",
            "location_type": "city",
            "entity_def_id": "location",
            "value": "Dublin"
          },
          {
            "permalink": "dublin-ireland",
            "uuid": "e401019b-70f7-46ee-f7f3-3331a2528672",
            "location_type": "region",
            "entity_def_id": "location",
            "value": "Dublin"
          },
          {
            "permalink": "ireland",
            "uuid": "1944e9da-82b4-8190-38c0-014fef22e2ef",
            "location_type": "country",
            "entity_def_id": "location",
            "value": "Ireland"
          },
          {
            "permalink": "europe",
            "uuid": "6106f5dc-823e-5da8-40d7-51612c0b2c4e",
            "location_type": "continent",
            "entity_def_id": "location",
            "value": "Europe"
          }
        ],
        "rank_event": 3816,
        "starts_on": "2016-09-22"
      },
      {
        "identifier": {
          "permalink": "saastock-on-tour-helsinki",
          "image_id": "sia5cwfirj01bj2twj9k",
          "uuid": "44962a8f-3b0c-493a-8c7c-01367e4d1dbe",
          "entity_def_id": "event",
          "value": "SaaStock on Tour: Helsinki"
        },
        "location_identifiers": [
          {
            "permalink": "helsinki-southern-finland",
            "uuid": "f1d17e2b-7516-24da-b4dc-9eb292782102",
            "location_type": "city",
            "entity_def_id": "location",
            "value": "Helsinki"
          },
          {
            "permalink": "southern-finland-finland",
            "uuid": "2291746f-af26-cd75-e9b5-b64e9df61781",
            "location_type": "region",
            "entity_def_id": "location",
            "value": "Southern Finland"
          },
          {
            "permalink": "finland",
            "uuid": "46a87674-f040-2806-b4bb-e9b83efe1070",
            "location_type": "country",
            "entity_def_id": "location",
            "value": "Finland"
          },
          {
            "permalink": "europe",
            "uuid": "6106f5dc-823e-5da8-40d7-51612c0b2c4e",
            "location_type": "continent",
            "entity_def_id": "location",
            "value": "Europe"
          }
        ],
        "rank_event": 5912,
        "starts_on": "2018-05-23"
      },
      {
        "identifier": {
          "permalink": "cargo-facts-emea-demovation-challenge",
          "image_id": "mujsswrnyjsyxhtsohtn",
          "uuid": "045690a1-d676-4d39-85a1-df5bfe341fac",
          "entity_def_id": "event",
          "value": "CARGO FACTS EMEA DEMOVATION CHALLENGE"
        },
        "location_identifiers": [
          {
            "permalink": "frankfurt-hessen",
            "uuid": "513f25f1-7f4b-e9c6-9fc2-e53b62af61da",
            "location_type": "city",
            "entity_def_id": "location",
            "value": "Frankfurt"
          },
          {
            "permalink": "hessen-germany",
            "uuid": "1ef4df3e-5386-ae5b-eff6-48fd795c7f2c",
            "location_type": "region",
            "entity_def_id": "location",
            "value": "Hessen"
          },
          {
            "permalink": "germany",
            "uuid": "6085b4bf-b18a-1763-a04e-fdde3f6aba94",
            "location_type": "country",
            "entity_def_id": "location",
            "value": "Germany"
          },
          {
            "permalink": "europe",
            "uuid": "6106f5dc-823e-5da8-40d7-51612c0b2c4e",
            "location_type": "continent",
            "entity_def_id": "location",
            "value": "Europe"
          }
        ],
        "rank_event": 9587,
        "starts_on": "2020-02-04"
      }
    ],
    "org_funding_rounds_list": [
      {
        "identifier": {
          "permalink": "deliverect-series-c--675bb09a",
          "image_id": "rpgsaioxf4nmvqq0akrm",
          "uuid": "675bb09a-ba01-4398-86d1-b95ba1600094",
          "entity_def_id": "funding_round",
          "value": "Series C - Deliverect"
        },
        "announced_on": "2021-04-21",
        "money_raised": {
          "value_usd": 65000000,
          "currency": "USD",
          "value": 65000000
        },
        "num_investors": 9
      },
      {
        "identifier": {
          "permalink": "n8n-io-series-a--53c9c399",
          "image_id": "khmh2ujewccz7ptsmb3g",
          "uuid": "53c9c399-17bf-4fbc-a8d1-d46b49161a0b",
          "entity_def_id": "funding_round",
          "value": "Series A - n8n.io"
        },
        "announced_on": "2021-04-26",
        "money_raised": {
          "value_usd": 12000000,
          "currency": "USD",
          "value": 12000000
        },
        "num_investors": 6
      },
      {
        "identifier": {
          "permalink": "glambook-angel--78f4b0cd",
          "image_id": "nxnnjkfn0pqd7dwfdyms",
          "uuid": "78f4b0cd-16bc-42e6-98cc-285f99ed40f0",
          "entity_def_id": "funding_round",
          "value": "Angel Round - Glambook"
        },
        "announced_on": "2021-05-07",
        "money_raised": {
          "value_usd": 608162,
          "currency": "EUR",
          "value": 500000
        },
        "num_investors": 2
      },
      {
        "identifier": {
          "permalink": "utmost-4235-series-b--b30bb725",
          "image_id": "feoaingkxrdtf1kl945x",
          "uuid": "b30bb725-c029-4f40-a7ea-7169fe317a03",
          "entity_def_id": "funding_round",
          "value": "Series B - Utmost"
        },
        "announced_on": "2021-05-05",
        "money_raised": {
          "value_usd": 21000000,
          "currency": "USD",
          "value": 21000000
        },
        "num_investors": 5
      },
      {
        "identifier": {
          "permalink": "bryter-series-b--5efa2dc0",
          "image_id": "vxicph4nxmmp5khp2o2h",
          "uuid": "5efa2dc0-d1e9-436c-9b17-0fdb67840243",
          "entity_def_id": "funding_round",
          "value": "Series B - BRYTER"
        },
        "announced_on": "2021-04-07",
        "money_raised": {
          "value_usd": 66000000,
          "currency": "USD",
          "value": 66000000
        },
        "num_investors": 5
      }
    ],
    "org_acquisitions_list": [
      {
        "identifier": {
          "permalink": "bambuser-acquires-relatable--906db6b9",
          "image_id": "nnaz2kv70rpykpe9kkmz",
          "uuid": "906db6b9-dcb2-4a86-b807-b965845aba6f",
          "entity_def_id": "acquisition",
          "value": "Relatable acquired by Bambuser"
        },
        "announced_on": {
          "precision": "day",
          "value": "2021-05-16"
        },
        "price": {
          "value_usd": 24000000,
          "currency": "USD",
          "value": 24000000
        },
        "acquirer_identifier": {
          "permalink": "bambuser",
          "role": "acquirer",
          "image_id": "uoi3fphr5wqsrfxnastp",
          "uuid": "7b704250-8308-86cf-9a6e-dde320af6f0c",
          "entity_def_id": "organization",
          "value": "Bambuser"
        }
      },
      {
        "identifier": {
          "permalink": "respond-1781-acquires-xmatters--de2b1f18",
          "image_id": "v1463051453/gnsjq4jirgymzbc9kfgp.png",
          "uuid": "de2b1f18-6c8b-401f-b735-7df161afff95",
          "entity_def_id": "acquisition",
          "value": "xMatters acquired by EverBridge"
        },
        "announced_on": {
          "precision": "day",
          "value": "2021-04-06"
        },
        "price": {
          "value_usd": 240000000,
          "currency": "USD",
          "value": 240000000
        },
        "acquirer_identifier": {
          "permalink": "respond-1781",
          "role": "acquirer",
          "image_id": "80385739e73578a6db54",
          "uuid": "ba1f64f5-8964-43ce-879b-abd3ce681781",
          "entity_def_id": "organization",
          "value": "EverBridge"
        }
      },
      {
        "identifier": {
          "permalink": "sidetrade-acquires-amalto-technologies--19226523",
          "image_id": "v1397181718/823e791e462d8c1aa94358df1a0150ee.jpg",
          "uuid": "19226523-848a-41dc-b68f-e0aab390ccc3",
          "entity_def_id": "acquisition",
          "value": "Amalto Technologies acquired by Sidetrade"
        },
        "announced_on": {
          "precision": "day",
          "value": "2021-04-06"
        },
        "price": {
          "value_usd": 16000000,
          "currency": "USD",
          "value": 16000000
        },
        "acquirer_identifier": {
          "permalink": "sidetrade",
          "role": "acquirer",
          "image_id": "ddd64npuivuu7r5dh1st",
          "uuid": "d108e3fc-34d1-4d52-be3d-8c9e8934bc4d",
          "entity_def_id": "organization",
          "value": "Sidetrade"
        }
      },
      {
        "identifier": {
          "permalink": "exact-acquires-gripp-0723--211a8f3e",
          "image_id": "jtfe9bm33kqjytucquf7",
          "uuid": "211a8f3e-2a17-4433-ac6c-a5b670d57317",
          "entity_def_id": "acquisition",
          "value": "Gripp acquired by Exact"
        },
        "announced_on": {
          "precision": "day",
          "value": "2021-04-11"
        },
        "acquirer_identifier": {
          "permalink": "exact",
          "role": "acquirer",
          "image_id": "v1503575088/ak42387cwmojqpgpedu8.png",
          "uuid": "8cb715b3-f39b-f444-3dea-cc20f4ee08bb",
          "entity_def_id": "organization",
          "value": "Exact"
        }
      },
      {
        "identifier": {
          "permalink": "friss-acquires-terrene-labs--44211d3e",
          "image_id": "kexovaqewcnyvicqkue1",
          "uuid": "44211d3e-ae4f-4356-b8f8-25b9cf3ed0f5",
          "entity_def_id": "acquisition",
          "value": "Terrene Labs acquired by FRISS"
        },
        "announced_on": {
          "precision": "day",
          "value": "2021-04-13"
        },
        "acquirer_identifier": {
          "permalink": "friss",
          "role": "acquirer",
          "image_id": "x6tctwfog5mzptzpavc7",
          "uuid": "87232cd2-55f3-fdab-9a2e-b9f601efdea6",
          "entity_def_id": "organization",
          "value": "FRISS"
        }
      }
    ],
    "overview_fields": {
      "locations": [
        {
          "uuid": "19e3ce8a-100d-44d8-89d7-8ca1be67361f",
          "value": "European Union (EU)",
          "permalink": "european-union-eu",
          "entity_def_id": "location",
          "location_type": "group"
        },
        {
          "uuid": "6106f5dc-823e-5da8-40d7-51612c0b2c4e",
          "value": "Europe",
          "permalink": "europe",
          "entity_def_id": "location",
          "location_type": "continent"
        }
      ],
      "org_num": 3280,
      "category_groups": [
        {
          "uuid": "85b6bca9-930a-11bc-a608-a513b76fb637",
          "value": "Software",
          "permalink": "software-85b6",
          "entity_def_id": "category_group"
        }
      ],
      "categories": [
        {
          "uuid": "5c4e6926-5ff7-b188-0892-c8eb036c5ace",
          "value": "SaaS",
          "permalink": "saas-5c4e",
          "entity_def_id": "category"
        }
      ],
      "rank_hub": 4597
    },
    "person_list": [
      {
        "identifier": {
          "permalink": "christian-reber",
          "image_id": "xn2f3xa3ki2vhasgaoxo",
          "uuid": "aab38224-f646-d320-bc93-ecccb244d500",
          "entity_def_id": "person",
          "value": "Christian Reber"
        },
        "primary_job_title": "Co-founder & CEO",
        "primary_organization": {
          "permalink": "pitch-5b94",
          "image_id": "zb9x7vydizz33c9gihwb",
          "uuid": "9417fb9b-7d04-4402-a99b-8e1e89105b94",
          "entity_def_id": "organization",
          "value": "Pitch"
        },
        "rank_person": 175
      },
      {
        "identifier": {
          "permalink": "thibaud-elziere",
          "image_id": "rftjrwrmhphqzrhn5emx",
          "uuid": "8d9b5e65-ddb3-4ac0-9be5-ca4e254948f1",
          "entity_def_id": "person",
          "value": "Thibaud Elziere"
        },
        "primary_job_title": "Co-Founder",
        "primary_organization": {
          "permalink": "upflow",
          "image_id": "thwg5cyza5fjv1ilixgz",
          "uuid": "a879138a-d001-49de-89cd-6b188ad8971c",
          "entity_def_id": "organization",
          "value": "Upflow"
        },
        "rank_person": 192
      },
      {
        "identifier": {
          "permalink": "bjorn-kolbmuller",
          "image_id": "ouuzd75ofhvzjgskkg43",
          "uuid": "6fc49a45-2926-1204-a8dc-e158a0d18fe5",
          "entity_def_id": "person",
          "value": "Bjorn Kolbmuller"
        },
        "primary_job_title": "Founder & Managing Director",
        "primary_organization": {
          "permalink": "zenloop",
          "image_id": "j7pcgetzuuvvsd0oylnb",
          "uuid": "fe0109c1-942b-4a12-a0f9-4cff2608321a",
          "entity_def_id": "organization",
          "value": "Zenloop"
        },
        "rank_person": 1174
      },
      {
        "identifier": {
          "permalink": "hanno-renner",
          "image_id": "v1486786714/vno3azngtbs5gcioeo6o.png",
          "uuid": "db711d5c-4c62-0fd2-0c0e-7ca3ce574584",
          "entity_def_id": "person",
          "value": "Hanno Renner"
        },
        "primary_job_title": "Chief Executive Officer",
        "primary_organization": {
          "permalink": "personio",
          "image_id": "dxda2fvk6myrsfbldvod",
          "uuid": "72f56787-8594-2e8b-192d-99d2479a5a4e",
          "entity_def_id": "organization",
          "value": "Personio"
        },
        "rank_person": 1744
      },
      {
        "identifier": {
          "permalink": "zhong-xu",
          "image_id": "iqsfr5zv01aelftja1j3",
          "uuid": "d272e90e-34b7-4584-2b4e-8fdcacf88ff5",
          "entity_def_id": "person",
          "value": "Zhong Xu"
        },
        "primary_job_title": "Co-Founder & CEO",
        "primary_organization": {
          "permalink": "deliverect",
          "image_id": "rpgsaioxf4nmvqq0akrm",
          "uuid": "4929db0a-9ec2-46b6-97b2-5253e203cade",
          "entity_def_id": "organization",
          "value": "Deliverect"
        },
        "rank_person": 2088
      }
    ],
    "overview_description": {
      "description": "Organizations in this hub have their headquarters located in European Union (EU), Europe; notable events and people located in European Union (EU) are also included.\n\nThis list of companies and startups in European Union (EU) in the saas space provides data on their funding history, investment activities, and acquisition trends. Insights about top trending companies, startups, investments and M&A activities, notable investors of these companies, their management team, and recent news are also included."
    },
    "principal_investments_headline": {
      "principal_num_investments": 346,
      "principal_num_lead_investments": 69
    },
    "org_ipos_headline": {
      "org_ipo_amount_raised_total": {
        "value": 110116273,
        "currency": "USD",
        "value_usd": 110116273
      },
      "org_num_ipos": 16
    },
    "org_investors_headline": {
      "org_num_investors": 4030,
      "org_num_lead_investors": 1347
    },
    "org_sub_organizations_headline": {
      "org_num_parent_organizations": 27,
      "org_num_sub_organizations": 36
    },
    "event_headline": {
      "event_num": 16
    },
    "org_investors_list": [
      {
        "identifier": {
          "permalink": "y-combinator",
          "image_id": "v1482160613/skm38vnvyl0wpgfyz98v.png",
          "uuid": "73633ee4-ea65-2967-6c5d-9b5fec7d2d5e",
          "entity_def_id": "organization",
          "value": "Y Combinator"
        },
        "location_identifiers": [
          {
            "permalink": "mountain-view-california",
            "uuid": "37bfe551-197e-0226-9a80-5d7bec8a50dd",
            "location_type": "city",
            "entity_def_id": "location",
            "value": "Mountain View"
          },
          {
            "permalink": "california-united-states",
            "uuid": "eb879a83-c91a-121e-0bb8-829782dbcf04",
            "location_type": "region",
            "entity_def_id": "location",
            "value": "California"
          },
          {
            "permalink": "united-states",
            "uuid": "f110fca2-1055-99f6-996d-011c198b3928",
            "location_type": "country",
            "entity_def_id": "location",
            "value": "United States"
          },
          {
            "permalink": "north-america",
            "uuid": "b25caef9-a1b8-3a5d-6232-93b2dfb6a1d1",
            "location_type": "continent",
            "entity_def_id": "location",
            "value": "North America"
          }
        ],
        "investor_type": [
          "accelerator"
        ]
      },
      {
        "identifier": {
          "permalink": "easme",
          "image_id": "cdkjbgppt8nstvla1b2r",
          "uuid": "1d0c86bf-c986-6b40-d757-4d97cdd5d877",
          "entity_def_id": "organization",
          "value": "EASME - EU Executive Agency for SMEs"
        },
        "location_identifiers": [
          {
            "permalink": "brussels-brussels-hoofdstedelijk-gewest",
            "uuid": "54a0994f-3c84-1dcd-81dd-f801dbb1c2b6",
            "location_type": "city",
            "entity_def_id": "location",
            "value": "Brussels"
          },
          {
            "permalink": "brussels-hoofdstedelijk-gewest-belgium",
            "uuid": "e5137655-8c65-1509-5644-0e23b1fda141",
            "location_type": "region",
            "entity_def_id": "location",
            "value": "Brussels Hoofdstedelijk Gewest"
          },
          {
            "permalink": "belgium",
            "uuid": "0bb46ca5-38e7-3977-5d09-34dd1143a806",
            "location_type": "country",
            "entity_def_id": "location",
            "value": "Belgium"
          },
          {
            "permalink": "europe",
            "uuid": "6106f5dc-823e-5da8-40d7-51612c0b2c4e",
            "location_type": "continent",
            "entity_def_id": "location",
            "value": "Europe"
          }
        ],
        "investor_type": [
          "government_office"
        ]
      },
      {
        "identifier": {
          "permalink": "techstars",
          "image_id": "sfdhykaf0zcn2oavawe5",
          "uuid": "3718597a-dd39-6661-3630-09cdd43bcac2",
          "entity_def_id": "organization",
          "value": "Techstars"
        },
        "location_identifiers": [
          {
            "permalink": "boulder-colorado",
            "uuid": "e208d0e6-1b9b-cf11-16e7-5feddc832cb5",
            "location_type": "city",
            "entity_def_id": "location",
            "value": "Boulder"
          },
          {
            "permalink": "colorado-united-states",
            "uuid": "056b6b39-09ea-2c85-27af-f54b58a28072",
            "location_type": "region",
            "entity_def_id": "location",
            "value": "Colorado"
          },
          {
            "permalink": "united-states",
            "uuid": "f110fca2-1055-99f6-996d-011c198b3928",
            "location_type": "country",
            "entity_def_id": "location",
            "value": "United States"
          },
          {
            "permalink": "north-america",
            "uuid": "b25caef9-a1b8-3a5d-6232-93b2dfb6a1d1",
            "location_type": "continent",
            "entity_def_id": "location",
            "value": "North America"
          }
        ],
        "investor_type": [
          "accelerator",
          "venture_capital"
        ]
      },
      {
        "identifier": {
          "permalink": "masschallenge",
          "image_id": "v1498553060/ehdyokwqilcqhancqwqs.png",
          "uuid": "183692b0-b175-b125-89ce-2badd9f56b55",
          "entity_def_id": "organization",
          "value": "MassChallenge"
        },
        "location_identifiers": [
          {
            "permalink": "boston-massachusetts",
            "uuid": "9898e533-996b-0514-8cc5-302f60454c02",
            "location_type": "city",
            "entity_def_id": "location",
            "value": "Boston"
          },
          {
            "permalink": "massachusetts-united-states",
            "uuid": "98c62fd9-2148-9dd7-d767-b27fa0816b97",
            "location_type": "region",
            "entity_def_id": "location",
            "value": "Massachusetts"
          },
          {
            "permalink": "united-states",
            "uuid": "f110fca2-1055-99f6-996d-011c198b3928",
            "location_type": "country",
            "entity_def_id": "location",
            "value": "United States"
          },
          {
            "permalink": "north-america",
            "uuid": "b25caef9-a1b8-3a5d-6232-93b2dfb6a1d1",
            "location_type": "continent",
            "entity_def_id": "location",
            "value": "North America"
          }
        ],
        "investor_type": [
          "accelerator"
        ]
      },
      {
        "identifier": {
          "permalink": "500-startups",
          "image_id": "v1400109019/ehscebzgx2cvshmw9vxb.jpg",
          "uuid": "56e40f50-97c7-2a77-255d-1d97d5f30646",
          "entity_def_id": "organization",
          "value": "500 Startups"
        },
        "location_identifiers": [
          {
            "permalink": "san-francisco-california",
            "uuid": "528f5e3c-90d1-1111-5d1c-2e4ff979d58e",
            "location_type": "city",
            "entity_def_id": "location",
            "value": "San Francisco"
          },
          {
            "permalink": "california-united-states",
            "uuid": "eb879a83-c91a-121e-0bb8-829782dbcf04",
            "location_type": "region",
            "entity_def_id": "location",
            "value": "California"
          },
          {
            "permalink": "united-states",
            "uuid": "f110fca2-1055-99f6-996d-011c198b3928",
            "location_type": "country",
            "entity_def_id": "location",
            "value": "United States"
          },
          {
            "permalink": "north-america",
            "uuid": "b25caef9-a1b8-3a5d-6232-93b2dfb6a1d1",
            "location_type": "continent",
            "entity_def_id": "location",
            "value": "North America"
          }
        ],
        "investor_type": [
          "accelerator",
          "venture_capital"
        ]
      }
    ],
    "org_recent_funding_rounds_list": [
      {
        "identifier": {
          "permalink": "pitch-5b94-series-b--aeea7cc9",
          "image_id": "zb9x7vydizz33c9gihwb",
          "uuid": "aeea7cc9-318f-4161-89bc-b6ce36cfd8eb",
          "entity_def_id": "funding_round",
          "value": "Series B - Pitch"
        },
        "announced_on": "2021-05-20",
        "money_raised": {
          "value_usd": 85000000,
          "currency": "USD",
          "value": 85000000
        },
        "funded_organization_identifier": {
          "permalink": "pitch-5b94",
          "role": "investee",
          "image_id": "zb9x7vydizz33c9gihwb",
          "uuid": "9417fb9b-7d04-4402-a99b-8e1e89105b94",
          "entity_def_id": "organization",
          "value": "Pitch"
        }
      },
      {
        "identifier": {
          "permalink": "apic-series-a--d286be62",
          "image_id": "dwdfru0ikonb5cwjpnfz",
          "uuid": "d286be62-e9bc-487d-ba58-f4c115a76a5f",
          "entity_def_id": "funding_round",
          "value": "Series A - Apicbase"
        },
        "announced_on": "2021-05-19",
        "money_raised": {
          "value_usd": 4896841,
          "currency": "EUR",
          "value": 4000000
        },
        "funded_organization_identifier": {
          "permalink": "apic",
          "role": "investee",
          "image_id": "dwdfru0ikonb5cwjpnfz",
          "uuid": "c542a27b-9412-f372-0e6d-0a1d4e0dbbf2",
          "entity_def_id": "organization",
          "value": "Apicbase"
        }
      },
      {
        "identifier": {
          "permalink": "shyftplan-series-a--a69fdd84",
          "image_id": "y8fneyrrjus4o4ogd4jd",
          "uuid": "a69fdd84-aa0d-4338-bd04-4961b6c246f0",
          "entity_def_id": "funding_round",
          "value": "Series A - shyftplan"
        },
        "announced_on": "2021-05-18",
        "money_raised": {
          "value_usd": 8523996,
          "currency": "EUR",
          "value": 7000000
        },
        "funded_organization_identifier": {
          "permalink": "shyftplan",
          "role": "investee",
          "image_id": "y8fneyrrjus4o4ogd4jd",
          "uuid": "e82e7695-5c44-f7d6-7cb7-2c7c9b859875",
          "entity_def_id": "organization",
          "value": "shyftplan"
        }
      },
      {
        "funded_organization_identifier": {
          "permalink": "nursebuddy",
          "role": "investee",
          "image_id": "g9vxehcne7jt1ujllcg0",
          "uuid": "28eff73d-ee24-9933-4201-baf69eef43d8",
          "entity_def_id": "organization",
          "value": "NurseBuddy"
        },
        "identifier": {
          "permalink": "nursebuddy-seed--b06623a0",
          "image_id": "g9vxehcne7jt1ujllcg0",
          "uuid": "b06623a0-f31d-4e5f-ac80-45dc45287d61",
          "entity_def_id": "funding_round",
          "value": "Seed Round - NurseBuddy"
        },
        "announced_on": "2021-05-18"
      },
      {
        "identifier": {
          "permalink": "aifora-seed--54ccad7c",
          "image_id": "nih4adn3jwoxua5o1lk3",
          "uuid": "54ccad7c-71a3-4640-b865-f50cf784f425",
          "entity_def_id": "funding_round",
          "value": "Seed Round - aifora"
        },
        "announced_on": "2021-05-17",
        "money_raised": {
          "value_usd": 8509800,
          "currency": "EUR",
          "value": 7000000
        },
        "funded_organization_identifier": {
          "permalink": "aifora",
          "role": "investee",
          "image_id": "nih4adn3jwoxua5o1lk3",
          "uuid": "7941f35a-83ca-429d-b6d4-245a7942a5f1",
          "entity_def_id": "organization",
          "value": "aifora"
        }
      }
    ],
    "principal_investments_fields": {
      "principal_num_investments_median": 2,
      "principal_num_lead_investments_median": 2
    }
  }
}
```
