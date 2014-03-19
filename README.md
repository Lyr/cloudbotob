- example of tagcloud to es:
curl -X POST "http://localhost:9200/botob/_search?search_type=count&pretty=true" -d '
{
    "query" : {
        "query_string": {
            "query": "fr",
            "fields": ["language"]
        }
    },
 
    "facets" : {
        "tagcloud" : {
            "terms" : { "field" : "text", "size" : 25, "script": "term.length() > 3 ? true: false", "exclude":["t.co","cest","http"] }
        }
    }
}'