# Epitopes.world front-end (AI for COVID-19 Vaccine)


This is the front-end of https://epitopes.world. It everything you see on the website.

The COVID-19 is a pandemic of humongous human and economic consequences. We have developed an AI algorithm that can help identify useful targets for a vaccine against COVID-19.

Testing vaccines is a very lengthy process and patient samples are rare, fragile and precious. By making our results public, our goal is to significantly reduce the pool of targets to be tested, thus accelerating the development of a vaccine.

All pages are static except the "Explore" page where the database is queried. In order to do so, a post request is sent to the back-end API server (https://api.epitopes.world/get-data) with a query payload: 

##### Payload query example:

```
{
	"payload": {
		"additional_fields":  [
			"Peptides.Sequence",
			"Peptides.Accession",
			"Peptides.Sub_accession",
			"Peptides.Name",
			"Peptides.Length"
		],
		"limit": 5000,
		"query": {
			"Peptides.Length": {
				"values": [8]
			},
			"Peptides.Name": {
				"values": ["SARS-CoV-1"]
			},
			"Peptides.Score": {
				"values": [0,1]
			}
		},
		"sort": {
			"direction": "RAND"
		}
	}
}
```


##### Query response example:

```
{
	"timestamp": 1589821186.1625593,
	"version": 0.1,
	"messages": [],
	"error": false,
	"errors": [],
	"payload": [
		{
			"Peptides.Score": 0.6104,
			"Peptides.Name": "SARS-CoV-2",
			"Peptides.Length": 9,
			"Peptides.Sequence": "VDTANPKTP",
			"Peptides.Accession": "NC_045512",
			"Peptides.Sub_accession": "CDS_of_YP_009724389.1"
		},
		{
			"Peptides.Score": 0.5113979999999999,
			"Peptides.Name": "SARS-CoV-2",
			"Peptides.Length": 9,
			"Peptides.Sequence": "CLDDRCILH",
			"Peptides.Accession": "NC_045512",
			"Peptides.Sub_accession": "CDS_of_YP_009724389.1"
		},
		{
			"Peptides.Score": 0.504951,
			"Peptides.Name": "SARS-CoV-2",
			"Peptides.Length": 9,
			"Peptides.Sequence": "EPTTTTSVP",
			"Peptides.Accession": "NC_045512",
			"Peptides.Sub_accession": "CDS_of_YP_009724391.1"
		},
                ...
	]
}
```

The content of payload is then used one the front-end side to populate the table and the graph. More information regarding the API could be found in the [COVAP back-end repo](https://github.com/tariqdaouda/covap-backend)



## Epitopes Front-end Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
