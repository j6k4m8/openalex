# openalex

This is an UNOFFICIAL client library designed to make it easy to interact with the [OpenAlex](https://openalex.org) API. The OpenAlex API is a free, open-source API that provides access to a wide range of data on academic publications, including metadata, citation data, and full-text content.

## Installation

To install this OpenAlex client library, you can use pip or uv. (I am choosing not to use the pypi `openalex` name to make it clear that this is an unofficial client library, but in the meantime the openalex name is not taken.)

```bash
uv add "git+https://github.com/j6k4m8/openalex"
```

## Usage

Here's a simple example of how you can use this library to search for publications on a particular topic:

```python
from openalex import OpenAlex

# Create a new OpenAlex client
client = OpenAlex(mailto="provide-an-email-for-better-service@example.com")

# Search for publications on a particular topic
author_uri = client.get_author_uri_by_search("jordan matelsky")

# Get author institutions:
client.get_author_institutions(author_uri)

```

Here, all objects are defined as Pydantic types, so you can access, for example, "deep" attributes like this:

```python
paper = client.get_work_by_search("dotmotif")
print(paper.title)
print(paper.authorships[0].author.id)
```

## See also

This work is used by the following projects:

| Project                                       | Description                                                                     |
| --------------------------------------------- | ------------------------------------------------------------------------------- |
| http://bib.experiments.kordinglab.com/nsf-coa | A simple NSF COA generator and collaborator-finder                              |
| https://github.com/j6k4m8/scholarversary      | milestone-finder for academic careers through the (limited!) lens of publishing |
| https://github.com/j6k4m8/remarkabib          | Emerging bibliography and reference manager for the reMarkable tablet.          |
