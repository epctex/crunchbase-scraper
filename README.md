# Crunchbase Scraper

## Crunchbase scraper

Since Crunchbase doesn't provide a proper and free API, this actor should help you to retrieve data from it.

The Crunchbase data scraper supports the following features:

-   **Scrape organization details** - You can scrape attributes like about, number of employees, technology, summary, people working or investment details of an organization. You can find details below.

-   **Scrape person details** - You can scrape attributes like title, name, CB Rank, primary organization, jobs or related hubs of a person. You can find details below.

-   **Scrape event details** - You can scrape attributes like speakers, name, location, date, venue and registration links of an event. You can find details below.

-   **Scrape hub details** - You can scrape attributes like number of founders, name, founded date, acquired percentage and so on. You can find details below.

-   **Scrape by keyword** - You can use location-wise keywords to search specific search lists. Also you can directly point out rental, for sale or sold properties on this feature.

## Possible Use-cases

-   **Competitor analysis:** You can use this actor to get detailed information about your competitors

-   **Data Analysis:** - You can analyse CrunchBase data any way you want from organizations to events.

-   **News and Signals:** Get news and signals from organizations

-   **Due Dillegence**

## Bugs, fixes, updates and changelog

This scraper is under active development. If you have any feature requests you can create an issue from [here](https://github.com/epctex/crunchbase-scraper/issues).

### Incoming Changes

-   Advanced search
-   Fetch full descriptions alongside short_description

## Input Parameters

The input of this scraper should be JSON containing the list of pages on Crunchbase that should be visited. Possible fields are:

- `search`: (Optional) (String) Keyword that can be searched in Crunchbase search engine. When it is present, `mode` must be used as well.

- `mode`: (Optional) (String) Mode of the actor. It gets the keyword from `search` parameter and initiate the search according to the mode. Can be `all`, `organizations`, `events`, `hubs` or `people`. When present, `search` must be provided as well.

- `startUrls`: (Optional) (Array) List of Crunchbase URLs. You should only provide organization detail, person detail, event detail or hub detail URLs.

- `maxItems`: (Optional) (Number) You can limit scraped items. This should be useful when you search through the big lists or search results.

- `proxy`: (Required) (Proxy Object) Proxy configuration.

- `extendOutputFunction`: (Optional) (String) Function that takes a JQuery handle ($) as argument and returns object with data.

- `customMapFunction`: (Optional) (String) Function that takes each objects handle as argument and returns object with executing the function.

This solution requires the use of **Proxy servers**, either your own proxy servers or you can use [Apify Proxy](https://www.apify.com/docs/proxy).

### Compute Unit Consumption

The actor optimized to run blazing fast and scrape many as items as possible. Therefore, it forefronts all item detail requests. If actor doesn't block very often it'll scrape 100 items in 1 minute with ~0.04-0.05 compute units.

### Crunchbase Scraper Input example

```json
{
    "startUrls": [
        "https://www.crunchbase.com/organization/warner-law-offices",
        "https://www.crunchbase.com/person/warner-l-baxter",
        "https://www.crunchbase.com/hub/warner-bros-alumni-founded-companies",
        "https://www.crunchbase.com/event/messenger-chatbots-the-secret-to-8x-engagement-20171010"
    ],
    "search": "warner",
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

## Example Crunchbase Items

An example structure of items in Crunchbase looks like this:

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
        "facet_ids": ["rank"],
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
        "event_appearances_headline": {},
    },
    "scrapedType": "person",
}
```
