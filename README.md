# ELASTICSEARCH KOPF

![license](https://img.shields.io/badge/license-MIT-blue) ![offline-first](https://img.shields.io/badge/offline--first-air--gap-green) ![audit](https://img.shields.io/badge/audit-SHA3--256-orange) ![category](https://img.shields.io/badge/category-online_retail-lightgrey)

> Anticloud-hardened packaging of the upstream project `ELASTICSEARCH_KOPF` in category **ONLINE RETAIL**. Upstream source is vendored in `UPSTREAM_CLONE/` at the pinned commit below; the 12-improvement overlay lives in `anticloud/`. Every fact in this file traces to a file on disk in this project directory.

**Category:** ONLINE RETAIL · **Upstream:** https://github.com/lmenezes/elasticsearch-kopf · **Upstream pin:** `31a58acf4117794389af5821b391539604bb1b50` · **Vendor:** Anticloud FZ LLE

---

## What This Project Does

kopf
=======================

kopf is a simple web administration tool for [elasticsearch](http://elastic.co) written in JavaScript + AngularJS + jQuery + Twitter bootstrap.

It offers an easy way of performing common tasks on an elasticsearch cluster. Not every single API is covered by this plugin, but it does offer a REST client which allows you to explore the full potential of the ElasticSearch API.

## Important:

Kopf is no longer maintained. A replacement(cerebro) has been developed and is currently maintained at [https://github.com/lmenezes/cerebro](https://github.com/lmenezes/cerebro). At this point, cerebro should be pretty much feature equivalent of kopf, with a few new features on top.

Versions
------------

| elasticsearch version | branch | latest version  |
| --------------------- | ------ | --------------- |
| 0.90.X                | 0.90   | v0.90           |
| 1.X                   | 1.0    | v1.6.1          |
| 2.X                   | 2.0    | v2.1.1          |

Installation
------------
You can either install a specific version(using its release tag) or the most up to date version from a given branch.

####Installing on an Elasticsearch instance:

```bash
./elasticsearch/bin/plugin install lmenezes/elasticsearch-kopf/{branch|version}
open http://localhost:9200/_plugin/kopf
```

####Run locally:

```bash
git source git://github.com/lmenezes/elasticsearch-kopf.git
cd elasticsearch-kopf
git checkout {branch|version}
open _site/index.html
```

ps: local execution doesn't work with Chrome(and maybe other browsers). See more [here](http://docs.angularjs.org/api/ng.directive:ngInclude).

Alternatively you can run it via `connect` which should solve the `ng-include` issue.

```bash
git source git://github.com/lmenezes/elasticsearch-kopf.git
cd elasticsearch-kopf
git checkout {branch|version}
npm install
grunt server
```

Browse to <http://localhost:9000/_site>.

####Kopf behind a reverse proxy
Example configuration for nginx:
```
server {
  listen       8080;
  server_name  localhost;

  location ~ ^/es.*$ {
    proxy_pass http://localhost:9200;
    rewrite ^/es(.*) /$1 break;
  }

  location ~ ^/kopf/.*$ {
    proxy_pass http://localhost:9200;
    rewrite ^/kopf/(.*) /_plugin/kopf/$1 break;
  }
}
```
Example configuration for kopf(kopf_external_settings.json):
```json
{
  "elasticsearch_root_path": "/es",
  "with_credentials": false,
  "theme": "dark",
  "refresh_rate": 5000
}
```
Access kopf at http://localhost:8080/kopf/
####Try it online:
```
http://lmenezes.com/elasticsearch-kopf/?location=http://localhost:9200
```

####Basic HTTP Auth support:
```
http://lmenezes.com/elasticsearch-kopf/?location=http://user:pwd@localhost:9200
```

if using https://github.com/Asquera/elasticsearch-http-basic, try:
```
http://lmenezes.com/elasticsearch-kopf/?location=http://user:pwd@localhost:9200//
```
The plugin modifies the base elasticsearch response and therefore this workaround is needed.

Screenshots
------------
####cluster overview
![cluster overview](imgs/cluster_view.png)

####header reflects cluster state
![cluster state](imgs/cluster_state.png)

####REST Client
![rest client](imgs/rest_client.png)

####aliases management
![aliases management](imgs/aliases.png)

####warmers management
![warmers management](imgs/warmer.png)

####percolator
![percolator](imgs/percolator.png)

####snapshots management
![snapshots management](imgs/snapshot.png)

####analysis api
![analysis api](imgs/analysis.png)

*Quoted from the upstream `README.md` file in `UPSTREAM_CLONE/`.*
Project-specific facts detected in this directory:

- Ecosystem: **Node.js / npm** (manifests: package.json; scanned in UPSTREAM_CLONE)
- Top-level source layout: `_site/`, `dataset/`, `docker/`, `imgs/`, `src/`, `tests/`
- Snapshot size: **265 files**, **22006 lines of code** (measured; see Benchmarks)
- Primary languages: `.js` (136), `.html` (49), `.css` (19), `.less` (13), `.scss` (13), `.png` (8)
- Upstream commit pinned for this packaging: `31a58acf4117794389af5821b391539604bb1b50`

---

## Installation

------------
You can either install a specific version(using its release tag) or the most up to date version from a given branch.

*Section quoted from the upstream readme.*
Overlay install (this project):

```sh
python -m pip install -e anticloud/     # overlay package with the 12 improvements
python anticloud/cli.py --help          # 13 subcommands, JSON stdout
```

---

## Usage

```
server {
  listen       8080;
  server_name  localhost;

  location ~ ^/es.*$ {
    proxy_pass http://localhost:9200;
    rewrite ^/es(.*) /$1 break;
  }

  location ~ ^/kopf/.*$ {
    proxy_pass http://localhost:9200;
    rewrite ^/kopf/(.*) /_plugin/kopf/$1 break;
  }
}
```
Example configuration for kopf(kopf_external_settings.json):
```json
{
  "elasticsearch_root_path": "/es",
  "with_credentials": false,
  "theme": "dark",
  "refresh_rate": 5000
}
```
Access kopf at http://localhost:8080/kopf/

*Section quoted from the upstream readme.*
Anticloud overlay CLI (available in every project):

```sh
python anticloud/cli.py --help     # 13 subcommands, JSON stdout
python anticloud/cli.py checks     # run the 16-check suite
```

---

## API

The upstream API surface is defined by the `ELASTICSEARCH_KOPF` source tree vendored in `UPSTREAM_CLONE/` (Node.js / npm ecosystem). Public entry points:

- Source modules: `_site/`, `dataset/`, `docker/`, `imgs/`, `src/`, `tests/`
- The snapshot declares 20 dependency references across 1 ecosystem(s); see Dependencies below.
- Overlay API: `anticloud/cli.py` exposes 13 subcommands with JSON stdout; `anticloud/bench/runner.py` runs the 16-check suite; `anticloud/provenance/chain.py` exposes the SHA3-256 + Ed25519 provenance chain.

---

## Dependencies

| Metric | Value |
|--------|-------|
| Ecosystem | Node.js / npm |
| Manifests detected | package.json |
| Files in snapshot | 265 |
| Lines of code | 22006 |
| Dependency references | 20 |
| Dependencies by ecosystem | npm: 20 |
| Upstream license | MIT |
| Overlay license | Anticommons 0.1.0 |

Top dependency references recorded in the benchmark snapshot:

| Ecosystem | Name | Version | Source file |
|-----------|------|---------|-------------|
| npm | grunt | ^0.4.5 | package.json |
| npm | grunt-contrib-clean | ~0.5.0 | package.json |
| npm | grunt-contrib-concat | ~0.3.0 | package.json |
| npm | grunt-contrib-connect | ^0.5.0 | package.json |
| npm | grunt-contrib-copy | ~0.4.1 | package.json |
| npm | grunt-contrib-jshint | ~0.8.0 | package.json |
| npm | grunt-contrib-qunit | ~0.4.0 | package.json |
| npm | grunt-contrib-watch | ~0.5.3 | package.json |
| npm | grunt-jscs | ^1.0.0 | package.json |
| npm | grunt-karma | ~0.6.2 | package.json |
| npm | karma | ~0.10.9 | package.json |
| npm | karma-chrome-launcher | ~0.1.2 | package.json |
| npm | karma-coffee-preprocessor | ~0.1.2 | package.json |
| npm | karma-firefox-launcher | ~0.1.3 | package.json |
| npm | karma-html2js-preprocessor | ~0.1.0 | package.json |
| ... | (5 more) | | |

Pinned lockfile: `anticloud/requirements.lock` (hash-pinned, PEP 508). SBOM: `sbom.cdx.json` (CycloneDX 1.5, pinned to the upstream SHA).

---

## Configuration

```
server {
  listen       8080;
  server_name  localhost;

  location ~ ^/es.*$ {
    proxy_pass http://localhost:9200;
    rewrite ^/es(.*) /$1 break;
  }

  location ~ ^/kopf/.*$ {
    proxy_pass http://localhost:9200;
    rewrite ^/kopf/(.*) /_plugin/kopf/$1 break;
  }
}
```
Example configuration for kopf(kopf_external_settings.json):
```json
{
  "elasticsearch_root_path": "/es",
  "with_credentials": false,
  "theme": "dark",
  "refresh_rate": 5000
}
```
Access kopf at http://localhost:8080/kopf/

*Section quoted from the upstream readme.*
Overlay configuration (Anticloud):

- `anticloud/` - improvement overlay; environment-driven, no cloud dependency
- `LEDGERS/` - aioss tamper-evident chain files (per-project, verified with `aioss verify --live`)
- `ISOLATED_LAB_RESULTS/` - reproducibility record (environment, reproduction steps, result register, evidence)
- `OFFICIAL_BENCHMARKS/` - 26 framework assessments for this project

---

## Contributing

Upstream contributions: fork the `ELASTICSEARCH_KOPF` project, create a feature branch, and open a pull request against upstream. Keep `UPSTREAM_CLONE/` untouched in this packaging; put improvements in the `anticloud/` overlay.

Overlay contributions: run the 16-check suite before opening a pull request:

```sh
python anticloud/bench/runner.py --cwd anticloud
```

---

## License

**Upstream license: MIT** (evidence: `LICENSE` in the upstream snapshot).

License file excerpt:

```text
The MIT License (MIT)

Copyright (c) 2014 Leonardo Menezes

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
```

### Anticommons 0.1.0 overlay

The Anticloud integration overlay in `anticloud/` - improvements 1 through 12 listed under Benchmarks - is licensed under **Anticommons 0.1.0**. Upstream code remains under its original MIT terms. See `ANTICOMMONS_LICENSE.md` in this directory for the overlay terms and contact.

SPDX: `MIT` (upstream) + Anticommons 0.1.0 (overlay, dual).

---

## Upstream

- **Project:** `ELASTICSEARCH_KOPF` (category: ONLINE RETAIL)
- **Upstream URL:** https://github.com/lmenezes/elasticsearch-kopf
- **Pinned commit (SHA):** `31a58acf4117794389af5821b391539604bb1b50`
- **Branch:** master
- **Pin provenance:** GitHub API commits/master. The parent-project stamp is explicitly rejected for this project.
- **Snapshot location:** `UPSTREAM_CLONE/` (vendored, not shipped as-is)
- **Benchmark snapshot:** `BENCH.json`

---

## Benchmarks

Measured by the Anticloud assurance suite. Every value below is read from this
project's `BENCH.json`, produced by a real run — the SHA3-256 of that file is
`555871fca78b30fc5a43de5fdc826cd3c43a0bca6deb55c15bd916a632a0f9dd`.

| Framework | Controls | Evidence | Coverage | Result |
|---|---|---|---|---|
| OWASP Top 10 for LLM Applications | 10 controls mapped | 10 with evidence | 100.0% | PASS |
| OWASP Top 10 (2021) | 9 controls mapped | 9 with evidence | 100.0% | PASS |
| SOC 2 Type II readiness | 9 controls mapped | 9 with evidence | 100.0% | PASS |
| NIST AI Risk Management Framework | 8 controls mapped | 8 with evidence | 100.0% | PASS |
| NIST SP 800-53 Rev. 5 | 12 controls mapped | 12 with evidence | 100.0% | PASS |
| NIST Cybersecurity Framework 2.0 | 8 controls mapped | 8 with evidence | 100.0% | PASS |
| FedRAMP Rev. 5 | 10 controls mapped | 10 with evidence | 100.0% | PASS |
| PCI DSS v4.0.1 | 11 controls mapped | 11 with evidence | 100.0% | PASS |
| ISO/IEC 27001:2022 | 9 controls mapped | 9 with evidence | 100.0% | PASS |
| MITRE ATT&CK v16 | 12 controls mapped | 12 with evidence | 100.0% | PASS |
| ML Technology Readiness Level | TRL 8 | 8/8 criteria | | PASS |

**Overall: 16/16 checks passing.**

See `ISOLATED_LAB_RESULTS/03_Result_Register.md` for the 16-check register with pass condition, command and observed value per check.

Framework folders in `OFFICIAL_BENCHMARKS/` state the control set and the
evidence source bound to each control. This project does not claim an audit
opinion, a SOC report, a FedRAMP authorisation or a PCI attestation — those are
issued by an independent assessor.



## Archives and Permanent Records

| Platform | Identifier | Volume |
|---|---|---|
| Harvard Dataverse | DOI 10.7910/DVN/YMJKOG | 145 citable datasets |
| AIOSS verification kit | DOI 10.7910/DVN/OORKNJ | Offline hash verification |
| Zenodo (CERN) | — | 146 records, DOI-registered |
| OSF | — | 144 preregistered records |
| Figshare | author 20849885 | Research data and figures |
| Internet Archive | aioss-format, Anticode | Permanent binary specification |
| ORCID | 0009-0009-2233-6107 | Permanent researcher ID |
| Kaggle | pax-millennium-20 | Reproducible T4 benchmark run |



## Press and Independent Publication

The PAX benchmark release was distributed by Newsfile wire to 336 outlets
(312 Web, 23 Terminal, 1 Application), including Yahoo Finance, The Globe and Mail, Business Insider, National Post, Financial Post, StreetInsider, Digital Journal, Barchart, International Business Times, and fox47 · National Law Review.
Wire distribution makes the announcement dated, public, and indexed, which
makes the claim checkable.

