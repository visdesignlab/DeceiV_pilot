# DeceiV_pilot

[This notebook](CleanedVisFilter.ipynb) is for splitting the collected data and preparing it for analysis.
It consists of three parts:
1. Data Cleaning: Here the downloaded images are sorted into 3 categories by a pre-trained model (laion2b_s34b_b79k), and the chart_or_graph category is the relevant one for our purposes.
2. Data Splitting and manual classification: The chart_or_graph images are randomly sampled by shuffling the original dataset and then picking the first 400. This shrunken dataset is then manually annotated, and the images are again filtered for their usability by a human.
3. Data analysis: The last part is inspecting the annotated data, which happens in the last cell. The resulting values are then reported (and printed after cell execution). In the annotation process the relevant columns are: `real or mis` which is labeled R for real information and M for mis or deceiving information, `opinionated` with Y for yes and N for no, `manual_topic` which is the topic we think it is, `isFromReputableSource` with Y for yes and N for no where reputable sources in our case, are sources like Eurostat, renowned newspapers, official news channels (ZIB), etc. 

The notebook was uploaded after execution. Hence, the results we have achieved are the displayed results in here.
Possibly not all required and also maybe redundant libraries in the first cell to be automatically installed.
Personal data has been removed before uploading the results, to properly execute the cells, require personal data has to be added (e.g., `YOUR_HUGGING_FACE_TOKEN`, `ROOT_DIR`, `CSV_PATH`). 
Originally we also sorted into the different platforms at first and performed image deduplication via hashes. However, since we do not provide the original images, we now assume that the images have been already sorted by their platform and contain the necessary data.


# Data Mapping:
### `all_platforms_image_manifest.csv`
| Column Name | Description |
| :--- | :--- |
|  `platform` | The platform the media appears on |
|  `row_index` | Local enumeration from all posts/messages |
|  `author` | Author or channel it was posted in |
|  `title` | Title of the post (Reddit only) |
|  `original_image_url` | URL directly to the image file |
|  `exact_post_url` | URL to the original post |
|  `channel` | Channel, subreddit, account, or feed posted on |

### `images_classified_results.csv`
| Column Name | Description |
| :--- | :--- |
|  `filename` | Local filename of the downloaded image |
|  `platform` | The platform the media appears on |
|  `original_image_url` | URL directly to the image file |
|  `exact_post_url` | URL to the original post |
|  `vis or not` | Visualization filter flag: **`T`** (is a visualization) or **`F`** (general image) |
|  `real or mis` | Authenticity classification: **`R`** (real vis) or **`M`** (deceptive / misinformation) |
|  `opinionated` | Opinion flag: **`Y`** (yes, opinionated) or **`N`** (no) |
|  `manual topic` | Manually assigned category or topic |
|  `notes` | Qualitative notes for classification |
|  `IsFromReputableSource` | Source credibility flag: **`Y`** (yes) or **`N`** (no) |
|  `channel` | Channel, subreddit, account, or feed posted on |