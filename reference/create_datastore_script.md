# Turn a GitHub release into a DataStore Script Reference

Given a GitHub owner ("nationalparkservice") and public repo
("EMLeditor"), the function uses the GitHub API to access the latest
release version on GitHub and generate a corresponding draft public
Script reference on DataStore.

WARNING: if you are not an author of the repo on GitHub, you should
probably NOT be the one adding it to DataStore unless you have very good
reason. If you want to cite a GitHub release/repo and need a DOI,
contact the repo maintainer and suggest they use this function to put it
on DataStore for you.

The function searches DataStore for references with a similar title
(where the title is repo + release tag). If `force = FALSE` and there
are similarly titled references, the function will return a list of them
and ask if the user really wants a new DataStore reference generated.
Assuming yes (or if there are no existing DataStore references with a
similar title or if `force = TRUE`), the function will:

1.  download the .zip of the latest GitHub release for the repo,

2.  initiate a draft reference on DataStore,

3.  give the draft reference a title (repo + release tag),

4.  upload the .zip from GitHub

5.  add a web link to the release on GitHub.

6.  add the items listed under GitHub repo "Topics" as keywords to the
    DataStore Script reference

7.  Set for or by NPS flag

8.  Set the issued date

9.  If you indicate it is an R package, the authors, steward,
    description, and other fields will be filled out on the Core tab \#'
    The user will still need to go access the draft Script reference on
    DataStore to fill in the remaining fields (which are not accessible
    via API and so cannot be automated through this function) and
    activate the reference (thereby generating and registering a
    citeable DOI).

If the Reference is a version of an older reference, the user will have
to access the older version and indicate that it is an older version of
the current Reference. The user will also have to manually add the new
Reference to a Project for the repo, if desired.

## Usage

``` r
create_datastore_script(
  owner,
  repo,
  lib_type = c("generic_script", "R", "python"),
  path = here::here(),
  force = FALSE,
  dev = FALSE,
  for_or_by_NPS = TRUE,
  chunk_size_mb = 1,
  retry = 1
)
```

## Arguments

- owner:

  String. The owner of the account where the GitHub repo resides. For
  example, "nationalparkservice"

- repo:

  String. The repo with a release that should be turned into a DataStore
  Script reference. For example, "EMLeditor"

- lib_type:

  String. Can be one of three values: generic_script, R, or python.
  Defaults to "generic_script".

- path:

  String. The location where the release .zip from GitHub should be
  downloaded to (and uploaded from). Defaults to the working directory
  of the R Project (i.e.
  [`here::here()`](https://here.r-lib.org/reference/here.html)).

- force:

  Logical. Defaults to FALSE. In the default status the function has a
  number of interactive components, such as searching DataStore for
  similarly titled References and asking if a new Reference is really
  what the user wants. When set to TRUE, all interactive components are
  turned off and the function will proceed unless it hits an error.
  Setting force = TRUE may be useful for scripting purposes.

- dev:

  Logical. Defaults to FALSE. In the default status, the function
  generates and populates a new draft Script reference on the DataStore
  production server. If set to TRUE, the draft Script reference will be
  generated and populated on the DataStore development server. Setting
  dev = TRUE may be useful for testing the function without generating
  excessive references on the DataStore production server.

- for_or_by_NPS:

  Logical. Was the code, script, or software created either for or by
  NPS? Defaults to TRUE.

- chunk_size_mb:

  The "chunk" size to break the file into for upload. If your network is
  slow and your uploads are failing, try decreasing this number (e.g.
  0.5 or 0.25).

- retry:

  How many times to retry uploading a file chunk if it fails on the
  first try.

## Value

Invisibly returns the URL to the DataStore draft reference that was
created.

## Examples

``` r
if (FALSE) { # \dontrun{
create_datastore_script("nationalparkservice", "EMLeditor")
} # }
```
