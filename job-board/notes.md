

# NM Job board

## URL

https://www.jobs.state.nm.us/vosnet/JobBanks/JobSearchCriteriaQuick.aspx

## API call

The job board makes an API call, which I captured with John Johnson-Rodger's help.
In brief, 

1. open above link
1. open Developer Tools
1. click the Network tab
1. back in the page, enter "Business Specialist II" in Job Title
1. click Search
1. back in Developer Tools, sort by Type field
1. click on the xhr type named "jobsearch.ashx" where the data: field in the Preview field is not Null
1. right-click on that same name, click Copy as cURL

See the request.txt file.

Run the curl using this:

```bash
bash requests.txt > response.json
```

Format the response with jq:

```bash
jq . response.json
```

The total number of responses:

```bash
cat response.json | jq .recordsTotal
```

The number of entries in this response:

```bash
cat zfoo.txt | jq '.data | length'
```