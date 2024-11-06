# When text meets image: a guide to OpenSearch for multimodal search

## Part 1. Prepare working environment

### Step 1. Set up OpenSearch service with Aiven

Register at [https://go.aiven.io/signup-opensearch-clip](https://go.aiven.io/signup-opensearch-clip) to host your OpenSearch service and get $400 credits for other services.

Follow the registration steps:

TODO

### Step 2. Set up Codespaces
Press the button to open this repository in GitHub Codespaces:

TODO

Or, if you prefer to do it manually: at the top of this GitHub page, above the file browser, select the <> Code button, choose the Codespaces tab and choose Create codespace on main. This will start up a new Codespaces environment.


### Step 3. Install Python libraries



## Part 2. Create OpenSearch index that supports KNN

To make sure that OpenSearch recognises vector data and supports KNN search, when creating an index we need to:
- set `knn` setting to true
- specify name of the property to contain vector data, set its type to `knn_vector` and specify its dimension size.

Go to `1-prepare-opensearch.ipynb` and run the notebook.

You should see the response 

```
{'acknowledged': True, 'shards_acknowledged': True, 'index': 'photos'}
```

Also a newly added index will appear in the list of indexes in the service page of your Aiven for OpenSearch service.

## Part 3. Process each image and upload the vectors to OpenSearch

In this step we'll load the CLIP model, compute feature vectors for a batch of images and send the data into OpenSearch.

Go to `2-process-and-upload.ipynb` and run the notebook steps one by one. The last step will take several minutes to iterate over the photos.

## Part 4. Search for images

Time to search for an image by providing a text description. For this we'll do the following:

1. Transpate the text into a vector using CLIP model.
2. Compare this single vector to the vectors for images that we stored in OpenSearch
3. Retrieve 3 nearest images to the vector that is searched for.

Go to `3-run-vector-search.ipynb` and run the notebook steps one by one. 
Change value of ``text_input`` to search for different images.

 
