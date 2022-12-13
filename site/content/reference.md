---
template: main.html
title: "BigFunctions"
ogtitle: "BigFunctions supercharge BigQuery"
description: "BigFunctions are open-source BigQuery routines that give you SQL-superpowers. BigFunctions can show data-visualizations inside BigQuery console, compute advanced transforms such as sentiment score of a text, or send data to any of your favorite SAAS tool. BigFunctions is dbt's best friend."
image: "https://unytics.io/bigfunctions/assets/logo_and_name.png"
image_alt: "Supercharge BigQuery with BigFunctions"
image_width: "2500"
image_height: "541"
hide:
  - navigation
---

## 📄 Overview

BigFunctions are open-source BigQuery routines that give you **SQL-superpowers** in BigQuery 💪.

!!! note ""



    

    **👀 Explore**

    
    - [<code>explore_column(fully_qualified_column)</code>](#explore_column): Show column statistics
    
    - [<code>explore_dataset(fully_qualified_dataset)</code>](#explore_dataset): Show infos about dataset tables
    
    - [<code>explore_table(fully_qualified_table)</code>](#explore_table): Show table infos and column statistics
    

    

    **✨ Transform string**

    
    - [<code>is_email_valid(email)</code>](#is_email_valid): Return true if `email` is valid
    
    - [<code>levenshtein(string1, string2)</code>](#levenshtein): Compute levenshtein distance between `string1` and `string2`
    
    - [<code>parse_url(url)</code>](#parse_url): Return `url` parts
    
    - [<code>remove_accents(str)</code>](#remove_accents): Remove accents
    
    - [<code>remove_extra_whitespaces(str)</code>](#remove_extra_whitespaces): Remove unwanted whitespaces
    
    - [<code>remove_strings(string, strings_to_remove)</code>](#remove_strings): Remove any string of `strings_to_remove` from `string`
    
    - [<code>remove_words(string, words_to_remove)</code>](#remove_words): Remove any word of `words_to_remove` from `string`
    
    - [<code>render_string(template, context)</code>](#render_string): Render template with context using nunjucks.js templating library
    
    - [<code>sentiment_score(content)</code>](#sentiment_score): Compute sentiment score of text
    

    

    **📆 Transform date**

    
    - [<code>is_public_holiday(date, country_code)</code>](#is_public_holiday): Return true if `date` corresponds to a public holiday in `country_code`
    
    - [<code>parse_date(date_string)</code>](#parse_date): Parse date with automatic format detection
    

    

    **<span style="color: var(--md-primary-fg-color);">{...}</span> Transform json**

    
    - [<code>json_items(json_string)</code>](#json_items): Extract `items` from `json_string`
    
    - [<code>json_keys(json_string)</code>](#json_keys): Extract `keys` from `json_string`
    
    - [<code>json_merge(json_string1, json_string2)</code>](#json_merge): Merge `json_string1` and `json_string2`
    
    - [<code>json_query(json_string, query)</code>](#json_query): Extract data from `json_string` using advanced json querying
    
    - [<code>json_schema(json_string)</code>](#json_schema): Return the schema of a json string as `[{path, type}]`
    
    - [<code>json_values(json_string)</code>](#json_values): Extract `values` from `json_string`
    

    

    **<span style="color: var(--md-primary-fg-color);">[...]</span> Transform array**

    
    - [<code>are_arrays_equal(array1, array2)</code>](#are_arrays_equal): Return true if `array1` = `array2`
    
    - [<code>distinct_values(arr)</code>](#distinct_values): Return distinct values
    
    - [<code>find_value(arr, value)</code>](#find_value): Return the first `offset` (zero-based index) of `value` in array `arr`
    
    - [<code>last_element(arr)</code>](#last_element): Return last element of array
    
    - [<code>max_value(arr)</code>](#max_value): Return max value of array
    
    - [<code>median_value(arr)</code>](#median_value): Return median value of array
    
    - [<code>min_value(arr)</code>](#min_value): Return min value of array
    
    - [<code>remove_value(arr, value)</code>](#remove_value): Return an array with all values except `value`.
    
    - [<code>sort_values(arr)</code>](#sort_values): Return sorted array (ascending)
    
    - [<code>sort_values_desc(arr)</code>](#sort_values_desc): Return sorted array (descending)
    
    - [<code>sum_values(arr)</code>](#sum_values): Return the sum of array values
    

    

    **🌐 Graph**

    
    - [<code>connected_components(fully_qualified_table)</code>](#connected_components): Compute the connected components of a non-directed graph.
    

    

    **💬 Notify**

    
    - [<code>notify_gmail(recipients, subject, body, attachment_filename, attachment_content)</code>](#notify_gmail): Send email via gmail
    

    

    **🚀 Export**

    
    - [<code>export_to_gmail(table_or_view_or_query, recipients, email_subject, email_body)</code>](#export_to_gmail): Send email (via gmail) with data attached as excel file
    

    

    **🔨 Utils**

    
    - [<code>chart(data, chart_type, ylabel)</code>](#chart): Return html with a chartjs chart
    
    - [<code>dump_to_excel(data)</code>](#dump_to_excel): Dump data to excel file returned as base64
    
    - [<code>get_json_column_schema(table_or_view_or_query, json_column)</code>](#get_json_column_schema): Return the schema of `json_column` of `table_or_view_or_query` as `[{path, type}]`
    
    - [<code>get_table_columns(fully_qualified_table)</code>](#get_table_columns): Get the column information of the given table from `INFORMATION_SCHEMA.COLUMNS`
    

    

    **🔴 Before using see --> [Getting Started](/bigfunctions/getting_started/)**






<div style="margin-top: 6rem;"></div>


## 👀 Explore

!!! note ""
    **Explore data within BigQuery console **

    Make computations on BigQuery and display the results as data-vizualizations directly in BigQuery console.

---



### explore_column
<div style="position: relative; top: -2rem; margin-bottom:  -2rem; text-align: right; z-index: 9999;">
  
  <a href="https://www.linkedin.com/in/paul-marcombes" title="Author: Paul Marcombes" target="_blank">
    <img src="https://media-exp1.licdn.com/dms/image/C4E03AQF92ENRMYC3Mw/profile-displayphoto-shrink_800_800/0/1656924490995?e=1675900800&v=beta&t=Ertn0DSUvqzexmymI6NDba3TrXaSLRM_cQ5dxjmTkzo" width="32" style=" border-radius: 50% !important">
  </a>
  
  <a href="https://github.com/unytics/bigfunctions/blob/main/bigfunctions/explore_column.yaml" title="Edit on GitHub" target="_blank"><svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24"><path fill="#5d6cc0" d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg></a></div>
```
explore_column(fully_qualified_column)
```

**Description**

Show column statistics

**Examples**






=== "US"

    ```sql
    call bigfunctions.us.explore_column("bigquery-public-data.samples.natality.weight_pounds");
    select html from bigfunction_result;
    ```








<a href="../assets/images/explore_column.png"><img alt="screenshot" src="../assets/images/explore_column.png" style="border: var(--md-code-bg-color) solid 1rem; margin-top: -1rem; width: 100%"></a>



---




### explore_dataset
<div style="position: relative; top: -2rem; margin-bottom:  -2rem; text-align: right; z-index: 9999;">
  
  <a href="https://www.linkedin.com/in/paul-marcombes" title="Author: Paul Marcombes" target="_blank">
    <img src="https://media-exp1.licdn.com/dms/image/C4E03AQF92ENRMYC3Mw/profile-displayphoto-shrink_800_800/0/1656924490995?e=1675900800&v=beta&t=Ertn0DSUvqzexmymI6NDba3TrXaSLRM_cQ5dxjmTkzo" width="32" style=" border-radius: 50% !important">
  </a>
  
  <a href="https://github.com/unytics/bigfunctions/blob/main/bigfunctions/explore_dataset.yaml" title="Edit on GitHub" target="_blank"><svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24"><path fill="#5d6cc0" d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg></a></div>
```
explore_dataset(fully_qualified_dataset)
```

**Description**

Show infos about dataset tables

**Examples**






=== "US"

    ```sql
    call bigfunctions.us.explore_dataset("bigquery-public-data.samples");
    select html from bigfunction_result;
    ```








<a href="../assets/images/explore_dataset.png"><img alt="screenshot" src="../assets/images/explore_dataset.png" style="border: var(--md-code-bg-color) solid 1rem; margin-top: -1rem; width: 100%"></a>



---




### explore_table
<div style="position: relative; top: -2rem; margin-bottom:  -2rem; text-align: right; z-index: 9999;">
  
  <a href="https://www.linkedin.com/in/paul-marcombes" title="Author: Paul Marcombes" target="_blank">
    <img src="https://media-exp1.licdn.com/dms/image/C4E03AQF92ENRMYC3Mw/profile-displayphoto-shrink_800_800/0/1656924490995?e=1675900800&v=beta&t=Ertn0DSUvqzexmymI6NDba3TrXaSLRM_cQ5dxjmTkzo" width="32" style=" border-radius: 50% !important">
  </a>
  
  <a href="https://github.com/unytics/bigfunctions/blob/main/bigfunctions/explore_table.yaml" title="Edit on GitHub" target="_blank"><svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24"><path fill="#5d6cc0" d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg></a></div>
```
explore_table(fully_qualified_table)
```

**Description**

Show table infos and column statistics

**Examples**






=== "US"

    ```sql
    call bigfunctions.us.explore_table("bigquery-public-data.samples.natality");
    select html from bigfunction_result;
    ```








<a href="../assets/images/explore_column.png"><img alt="screenshot" src="../assets/images/explore_column.png" style="border: var(--md-code-bg-color) solid 1rem; margin-top: -1rem; width: 100%"></a>



---









<div style="margin-top: 6rem;"></div>


## ✨ Transform string

!!! note ""
    **Transform data creatively **

    Be amazed with your new SQL powers.

---



### is_email_valid
<div style="position: relative; top: -2rem; margin-bottom:  -2rem; text-align: right; z-index: 9999;">
  
  <a href="https://www.linkedin.com/in/chris-j-goddard/" title="Credits: Chris Goddard" target="_blank">
    <img src="https://media-exp1.licdn.com/dms/image/C4D03AQGC7iFJlo7zUA/profile-displayphoto-shrink_200_200/0/1603420752762?e=1675900800&v=beta&t=9UU_ofvohzGANcMoZ7O5YR_y8DUg4ayAylSA9sWOESM" width="32" style=" border-radius: 50% !important">
  </a>
  
  <a href="https://github.com/unytics/bigfunctions/blob/main/bigfunctions/is_email_valid.yaml" title="Edit on GitHub" target="_blank"><svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24"><path fill="#5d6cc0" d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg></a></div>
```
is_email_valid(email)
```

**Description**

Return true if `email` is valid
*(inspired from [this reddit answer](https://www.reddit.com/r/bigquery/comments/dshge0/comment/f6r7rpt/))*

**Examples**



<span style="color: var(--md-typeset-a-color);">1. with a valid email</span>


=== "EU"

    ```sql
    select bigfunctions.eu.is_email_valid('paul.marcombes@unytics.io') as is_email_valid

    ```


=== "US"

    ```sql
    select bigfunctions.us.is_email_valid('paul.marcombes@unytics.io') as is_email_valid

    ```


=== "europe-west1"

    ```sql
    select bigfunctions.europe_west1.is_email_valid('paul.marcombes@unytics.io') as is_email_valid

    ```


=== "your-region2"

    ```sql
    select bigfunctions.your_region2.is_email_valid('paul.marcombes@unytics.io') as is_email_valid

    ```





<pre style="margin-top: -1rem;">
<code style="padding-top: 0px; padding-bottom: 0px;">+----------------+
| is_email_valid |
+----------------+
| true           |
+----------------+
</code>
</pre>









<span style="color: var(--md-typeset-a-color);">2. with incorrect format</span>


=== "EU"

    ```sql
    select bigfunctions.eu.is_email_valid('paul/marcombes@example.com') as is_email_valid

    ```


=== "US"

    ```sql
    select bigfunctions.us.is_email_valid('paul/marcombes@example.com') as is_email_valid

    ```


=== "europe-west1"

    ```sql
    select bigfunctions.europe_west1.is_email_valid('paul/marcombes@example.com') as is_email_valid

    ```


=== "your-region2"

    ```sql
    select bigfunctions.your_region2.is_email_valid('paul/marcombes@example.com') as is_email_valid

    ```





<pre style="margin-top: -1rem;">
<code style="padding-top: 0px; padding-bottom: 0px;">+----------------+
| is_email_valid |
+----------------+
| false          |
+----------------+
</code>
</pre>









<span style="color: var(--md-typeset-a-color);">3. with a domain not registrable</span>


=== "EU"

    ```sql
    select bigfunctions.eu.is_email_valid('paul.marcombes@example.con') as is_email_valid

    ```


=== "US"

    ```sql
    select bigfunctions.us.is_email_valid('paul.marcombes@example.con') as is_email_valid

    ```


=== "europe-west1"

    ```sql
    select bigfunctions.europe_west1.is_email_valid('paul.marcombes@example.con') as is_email_valid

    ```


=== "your-region2"

    ```sql
    select bigfunctions.your_region2.is_email_valid('paul.marcombes@example.con') as is_email_valid

    ```





<pre style="margin-top: -1rem;">
<code style="padding-top: 0px; padding-bottom: 0px;">+----------------+
| is_email_valid |
+----------------+
| false          |
+----------------+
</code>
</pre>










---




### levenshtein
<div style="position: relative; top: -2rem; margin-bottom:  -2rem; text-align: right; z-index: 9999;">
  
  <a href="https://www.linkedin.com/in/paul-marcombes" title="Author: Paul Marcombes" target="_blank">
    <img src="https://media-exp1.licdn.com/dms/image/C4E03AQF92ENRMYC3Mw/profile-displayphoto-shrink_800_800/0/1656924490995?e=1675900800&v=beta&t=Ertn0DSUvqzexmymI6NDba3TrXaSLRM_cQ5dxjmTkzo" width="32" style=" border-radius: 50% !important">
  </a>
  
  <a href="https://github.com/unytics/bigfunctions/blob/main/bigfunctions/levenshtein.yaml" title="Edit on GitHub" target="_blank"><svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24"><path fill="#5d6cc0" d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg></a></div>
```
levenshtein(string1, string2)
```

**Description**

Compute levenshtein distance between `string1` and `string2`

**Examples**






=== "EU"

    ```sql
    select bigfunctions.eu.levenshtein('bak', 'book') as distance

    ```


=== "US"

    ```sql
    select bigfunctions.us.levenshtein('bak', 'book') as distance

    ```


=== "europe-west1"

    ```sql
    select bigfunctions.europe_west1.levenshtein('bak', 'book') as distance

    ```


=== "your-region2"

    ```sql
    select bigfunctions.your_region2.levenshtein('bak', 'book') as distance

    ```





<pre style="margin-top: -1rem;">
<code style="padding-top: 0px; padding-bottom: 0px;">+----------+
| distance |
+----------+
| 2        |
+----------+
</code>
</pre>










---




### parse_url
<div style="position: relative; top: -2rem; margin-bottom:  -2rem; text-align: right; z-index: 9999;">
  
  <a href="https://www.linkedin.com/in/taylorabrownlow/" title="Credits: Taylor Brownlow" target="_blank">
    <img src="https://media-exp1.licdn.com/dms/image/C4E03AQFCRlj44wnbhA/profile-displayphoto-shrink_200_200/0/1579795128165?e=1672272000&v=beta&t=LxL7tn53S_dQU0jMAeT3lHiAP4anA8GSiYD71u63pMs" width="32" style=" border-radius: 50% !important">
  </a>
  
  <a href="https://github.com/unytics/bigfunctions/blob/main/bigfunctions/parse_url.yaml" title="Edit on GitHub" target="_blank"><svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24"><path fill="#5d6cc0" d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg></a></div>
```
parse_url(url)
```

**Description**

Return `url` parts
*(inspired from [sql-snippets repo](https://github.com/count/sql-snippets/blob/main/bigquery/regex-parse-url.md))*

**Examples**






=== "EU"

    ```sql
    select bigfunctions.eu.parse_url('https://www.yoursite.com/pricing/details?myparam1=123&myparam2=abc#newsfeed') as url_parts

    ```


=== "US"

    ```sql
    select bigfunctions.us.parse_url('https://www.yoursite.com/pricing/details?myparam1=123&myparam2=abc#newsfeed') as url_parts

    ```


=== "europe-west1"

    ```sql
    select bigfunctions.europe_west1.parse_url('https://www.yoursite.com/pricing/details?myparam1=123&myparam2=abc#newsfeed') as url_parts

    ```


=== "your-region2"

    ```sql
    select bigfunctions.your_region2.parse_url('https://www.yoursite.com/pricing/details?myparam1=123&myparam2=abc#newsfeed') as url_parts

    ```





<pre style="margin-top: -1rem;">
<code style="padding-top: 0px; padding-bottom: 0px;">+------------------------------------------------------------------------------------------------------------------------------------------------------+
| url_parts                                                                                                                                            |
+------------------------------------------------------------------------------------------------------------------------------------------------------+
| struct<'www.yoursite.com' as host, 'pricing/details' as path, 'myparam1=123&myparam2=abc#newsfeed' as query, 'newsfeed' as ref, 'https' as protocol> |
+------------------------------------------------------------------------------------------------------------------------------------------------------+
</code>
</pre>










---




### remove_accents
<div style="position: relative; top: -2rem; margin-bottom:  -2rem; text-align: right; z-index: 9999;">
  
  <a href="https://www.linkedin.com/company/esmoz/" title="Author: Sid Ali" target="_blank">
    <img src="https://media-exp1.licdn.com/dms/image/C560BAQHFcSF8X1MqrQ/company-logo_200_200/0/1636992707472?e=1678320000&v=beta&t=BJmNI_Nd0GuC9Mn3wKc1xGUEpZsCy-CsrTZh47cPcOQ" width="32" style=" border-radius: 50% !important">
  </a>
  
  <a href="https://github.com/unytics/bigfunctions/blob/main/bigfunctions/remove_accents.yaml" title="Edit on GitHub" target="_blank"><svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24"><path fill="#5d6cc0" d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg></a></div>
```
remove_accents(str)
```

**Description**

Remove accents

**Examples**






=== "EU"

    ```sql
    select bigfunctions.eu.remove_accents('Voilà !') as cleaned_string

    ```


=== "US"

    ```sql
    select bigfunctions.us.remove_accents('Voilà !') as cleaned_string

    ```


=== "europe-west1"

    ```sql
    select bigfunctions.europe_west1.remove_accents('Voilà !') as cleaned_string

    ```


=== "your-region2"

    ```sql
    select bigfunctions.your_region2.remove_accents('Voilà !') as cleaned_string

    ```





<pre style="margin-top: -1rem;">
<code style="padding-top: 0px; padding-bottom: 0px;">+----------------+
| cleaned_string |
+----------------+
| Voila !        |
+----------------+
</code>
</pre>










---




### remove_extra_whitespaces
<div style="position: relative; top: -2rem; margin-bottom:  -2rem; text-align: right; z-index: 9999;">
  
  <a href="https://www.linkedin.com/company/redata/" title="Author: re_data" target="_blank">
    <img src="https://media-exp1.licdn.com/dms/image/C4E0BAQFYSyHBVMp96w/company-logo_200_200/0/1625304367962?e=1674691200&v=beta&t=YlLm-FImlG2r3ziS8O1pP5FlIj7_IsxnaDvUVFw0__A" width="32" style=" border-radius: 50% !important">
  </a>
  
  <a href="https://github.com/unytics/bigfunctions/blob/main/bigfunctions/remove_extra_whitespaces.yaml" title="Edit on GitHub" target="_blank"><svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24"><path fill="#5d6cc0" d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg></a></div>
```
remove_extra_whitespaces(str)
```

**Description**

Remove unwanted whitespaces
*(inspired from [re_data dbt repo](https://github.com/re-data/dbt-re-data/blob/main/macros/public/cleaning/clean_additional_whitespace.sql))*

**Examples**






=== "EU"

    ```sql
    select bigfunctions.eu.remove_extra_whitespaces('Hi   Madison  and Mateusz!\n How are you doing?') as cleaned_string

    ```


=== "US"

    ```sql
    select bigfunctions.us.remove_extra_whitespaces('Hi   Madison  and Mateusz!\n How are you doing?') as cleaned_string

    ```


=== "europe-west1"

    ```sql
    select bigfunctions.europe_west1.remove_extra_whitespaces('Hi   Madison  and Mateusz!\n How are you doing?') as cleaned_string

    ```


=== "your-region2"

    ```sql
    select bigfunctions.your_region2.remove_extra_whitespaces('Hi   Madison  and Mateusz!\n How are you doing?') as cleaned_string

    ```





<pre style="margin-top: -1rem;">
<code style="padding-top: 0px; padding-bottom: 0px;">+--------------------------------------------+
| cleaned_string                             |
+--------------------------------------------+
| Hi Madison and Mateusz! How are you doing? |
+--------------------------------------------+
</code>
</pre>










---




### remove_strings
<div style="position: relative; top: -2rem; margin-bottom:  -2rem; text-align: right; z-index: 9999;">
  
  <a href="https://www.linkedin.com/in/benjamin-tabet" title="Author: Benjamin Tabet" target="_blank">
    <img src="https://media-exp1.licdn.com/dms/image/C4D03AQGWnyJdEmZeZw/profile-displayphoto-shrink_400_400/0/1667928305931?e=1673481600&v=beta&t=sxH1fFMPjj9ASbqfQ6TkIpWKk_PQ0hUAhOtuAs2zTu0" width="32" style=" border-radius: 50% !important">
  </a>
  
  <a href="https://github.com/unytics/bigfunctions/blob/main/bigfunctions/remove_strings.yaml" title="Edit on GitHub" target="_blank"><svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24"><path fill="#5d6cc0" d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg></a></div>
```
remove_strings(string, strings_to_remove)
```

**Description**

Remove any string of `strings_to_remove` from `string`

**Examples**






=== "EU"

    ```sql
    select bigfunctions.eu.remove_strings('I can eat candies', ['can', 'eat']) as cleaned_string

    ```


=== "US"

    ```sql
    select bigfunctions.us.remove_strings('I can eat candies', ['can', 'eat']) as cleaned_string

    ```


=== "europe-west1"

    ```sql
    select bigfunctions.europe_west1.remove_strings('I can eat candies', ['can', 'eat']) as cleaned_string

    ```


=== "your-region2"

    ```sql
    select bigfunctions.your_region2.remove_strings('I can eat candies', ['can', 'eat']) as cleaned_string

    ```





<pre style="margin-top: -1rem;">
<code style="padding-top: 0px; padding-bottom: 0px;">+----------------+
| cleaned_string |
+----------------+
| I  dies        |
+----------------+
</code>
</pre>










---




### remove_words
<div style="position: relative; top: -2rem; margin-bottom:  -2rem; text-align: right; z-index: 9999;">
  
  <a href="https://www.linkedin.com/in/benjamin-tabet" title="Author: Benjamin Tabet" target="_blank">
    <img src="https://media-exp1.licdn.com/dms/image/C4D03AQGWnyJdEmZeZw/profile-displayphoto-shrink_400_400/0/1667928305931?e=1673481600&v=beta&t=sxH1fFMPjj9ASbqfQ6TkIpWKk_PQ0hUAhOtuAs2zTu0" width="32" style=" border-radius: 50% !important">
  </a>
  
  <a href="https://github.com/unytics/bigfunctions/blob/main/bigfunctions/remove_words.yaml" title="Edit on GitHub" target="_blank"><svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24"><path fill="#5d6cc0" d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg></a></div>
```
remove_words(string, words_to_remove)
```

**Description**

Remove any word of `words_to_remove` from `string`

**Examples**






=== "EU"

    ```sql
    select bigfunctions.eu.remove_words('I can eat candies', ['can', 'eat']) as cleaned_string

    ```


=== "US"

    ```sql
    select bigfunctions.us.remove_words('I can eat candies', ['can', 'eat']) as cleaned_string

    ```


=== "europe-west1"

    ```sql
    select bigfunctions.europe_west1.remove_words('I can eat candies', ['can', 'eat']) as cleaned_string

    ```


=== "your-region2"

    ```sql
    select bigfunctions.your_region2.remove_words('I can eat candies', ['can', 'eat']) as cleaned_string

    ```





<pre style="margin-top: -1rem;">
<code style="padding-top: 0px; padding-bottom: 0px;">+----------------+
| cleaned_string |
+----------------+
| I  candies     |
+----------------+
</code>
</pre>










---




### render_string
<div style="position: relative; top: -2rem; margin-bottom:  -2rem; text-align: right; z-index: 9999;">
  
  <a href="https://www.linkedin.com/in/paul-marcombes" title="Author: Paul Marcombes" target="_blank">
    <img src="https://media-exp1.licdn.com/dms/image/C4E03AQF92ENRMYC3Mw/profile-displayphoto-shrink_800_800/0/1656924490995?e=1675900800&v=beta&t=Ertn0DSUvqzexmymI6NDba3TrXaSLRM_cQ5dxjmTkzo" width="32" style=" border-radius: 50% !important">
  </a>
  
  <a href="https://github.com/unytics/bigfunctions/blob/main/bigfunctions/render_string.yaml" title="Edit on GitHub" target="_blank"><svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24"><path fill="#5d6cc0" d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg></a></div>
```
render_string(template, context)
```

**Description**

Render template with context using nunjucks.js templating library

**Examples**






=== "EU"

    ```sql
    select bigfunctions.eu.render_string('Hello {{ username }}', '{"username": "James"}') as rendered_content

    ```


=== "US"

    ```sql
    select bigfunctions.us.render_string('Hello {{ username }}', '{"username": "James"}') as rendered_content

    ```


=== "europe-west1"

    ```sql
    select bigfunctions.europe_west1.render_string('Hello {{ username }}', '{"username": "James"}') as rendered_content

    ```


=== "your-region2"

    ```sql
    select bigfunctions.your_region2.render_string('Hello {{ username }}', '{"username": "James"}') as rendered_content

    ```





<pre style="margin-top: -1rem;">
<code style="padding-top: 0px; padding-bottom: 0px;">+------------------+
| rendered_content |
+------------------+
| Hello James      |
+------------------+
</code>
</pre>










---




### sentiment_score
<div style="position: relative; top: -2rem; margin-bottom:  -2rem; text-align: right; z-index: 9999;">
  
  <a href="https://www.linkedin.com/in/paul-marcombes" title="Author: Paul Marcombes" target="_blank">
    <img src="https://media-exp1.licdn.com/dms/image/C4E03AQF92ENRMYC3Mw/profile-displayphoto-shrink_800_800/0/1656924490995?e=1675900800&v=beta&t=Ertn0DSUvqzexmymI6NDba3TrXaSLRM_cQ5dxjmTkzo" width="32" style=" border-radius: 50% !important">
  </a>
  
  <a href="https://github.com/unytics/bigfunctions/blob/main/bigfunctions/sentiment_score.yaml" title="Edit on GitHub" target="_blank"><svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24"><path fill="#5d6cc0" d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg></a></div>
```
sentiment_score(content)
```

**Description**

Compute sentiment score of text

**Examples**






=== "EU"

    ```sql
    select bigfunctions.eu.sentiment_score('BigFunctions Rock!') as sentiment_score

    ```


=== "US"

    ```sql
    select bigfunctions.us.sentiment_score('BigFunctions Rock!') as sentiment_score

    ```


=== "europe-west1"

    ```sql
    select bigfunctions.europe_west1.sentiment_score('BigFunctions Rock!') as sentiment_score

    ```


=== "your-region2"

    ```sql
    select bigfunctions.your_region2.sentiment_score('BigFunctions Rock!') as sentiment_score

    ```





<pre style="margin-top: -1rem;">
<code style="padding-top: 0px; padding-bottom: 0px;">+-----------------+
| sentiment_score |
+-----------------+
| 0.945           |
+-----------------+
</code>
</pre>










---









<div style="margin-top: 6rem;"></div>


## 📆 Transform date

!!! note ""
    **Transform data creatively **

    Be amazed with your new SQL powers.

---



### is_public_holiday
<div style="position: relative; top: -2rem; margin-bottom:  -2rem; text-align: right; z-index: 9999;">
  
  <a href="https://www.linkedin.com/in/paul-marcombes" title="Author: Paul Marcombes" target="_blank">
    <img src="https://media-exp1.licdn.com/dms/image/C4E03AQF92ENRMYC3Mw/profile-displayphoto-shrink_800_800/0/1656924490995?e=1675900800&v=beta&t=Ertn0DSUvqzexmymI6NDba3TrXaSLRM_cQ5dxjmTkzo" width="32" style=" border-radius: 50% !important">
  </a>
  
  <a href="https://github.com/unytics/bigfunctions/blob/main/bigfunctions/is_public_holiday.yaml" title="Edit on GitHub" target="_blank"><svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24"><path fill="#5d6cc0" d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg></a></div>
```
is_public_holiday(date, country_code)
```

**Description**

Return true if `date` corresponds to a public holiday in `country_code`

- Always return `false` if date is not between year 1974 and year 2076.
- `country_code` must be among `[AO, AR, AW, AU, AT, AZ, BD, BY, BE, BO, BW, BR, BG, BI, CA, CL, CN, CO, HR, CU, CW, CY, CZ, DK, DJ, DO, EG, EE, ET, FI, FR, GE, DE, GR, HN, HK, HU, IS, IN, IE, IL, IT, JM, JP, KZ, KE, KR, LV, LS, LT, LU, MG, MW, MY, MT, MX, MD, MA, MZ, NA, NL, NZ, NI, NG, MK, NO, PY, PE, PL, PT, RO, RU, SA, RS, SG, SK, SI, ZA, ES, SZ, SE, CH, TW, TN, TR, UA, AE, GB, US, UY, UZ, VE, VN, ZM, ZW]`
- Holiday dates come from <a href="https://python-holidays.readthedocs.io/" target="_blank">`python-holidays`</a>.


**Examples**






=== "EU"

    ```sql
    select bigfunctions.eu.is_public_holiday(date('2022-07-14'), 'FR') as is_public_holiday

    ```


=== "US"

    ```sql
    select bigfunctions.us.is_public_holiday(date('2022-07-14'), 'FR') as is_public_holiday

    ```


=== "europe-west1"

    ```sql
    select bigfunctions.europe_west1.is_public_holiday(date('2022-07-14'), 'FR') as is_public_holiday

    ```


=== "your-region2"

    ```sql
    select bigfunctions.your_region2.is_public_holiday(date('2022-07-14'), 'FR') as is_public_holiday

    ```





<pre style="margin-top: -1rem;">
<code style="padding-top: 0px; padding-bottom: 0px;">+-------------------+
| is_public_holiday |
+-------------------+
| true              |
+-------------------+
</code>
</pre>










---




### parse_date
<div style="position: relative; top: -2rem; margin-bottom:  -2rem; text-align: right; z-index: 9999;">
  
  <a href="https://www.linkedin.com/in/sebo-banerjee/" title="Credits: Sebabrata Banerjee" target="_blank">
    <img src="https://media-exp1.licdn.com/dms/image/C4D03AQHFfCabt6UuLw/profile-displayphoto-shrink_200_200/0/1662473522711?e=1672272000&v=beta&t=hlhzWEk4UwQyaZmwNN1u9_F3DeRCLNwYgQrym-OiMC8" width="32" style=" border-radius: 50% !important">
  </a>
  
  <a href="https://github.com/unytics/bigfunctions/blob/main/bigfunctions/parse_date.yaml" title="Edit on GitHub" target="_blank"><svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24"><path fill="#5d6cc0" d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg></a></div>
```
parse_date(date_string)
```

**Description**

Parse date with automatic format detection
*(inspired from [Sebabrata BigQuery tutorial](https://www.linkedin.com/feed/update/urn:li:activity:6989555205612670976/))*

**Examples**






=== "EU"

    ```sql
    select bigfunctions.eu.parse_date('2021-01-20 ') as cleaned_date

    ```


=== "US"

    ```sql
    select bigfunctions.us.parse_date('2021-01-20 ') as cleaned_date

    ```


=== "europe-west1"

    ```sql
    select bigfunctions.europe_west1.parse_date('2021-01-20 ') as cleaned_date

    ```


=== "your-region2"

    ```sql
    select bigfunctions.your_region2.parse_date('2021-01-20 ') as cleaned_date

    ```





<pre style="margin-top: -1rem;">
<code style="padding-top: 0px; padding-bottom: 0px;">+--------------------+
| cleaned_date       |
+--------------------+
| date('2021-01-20') |
+--------------------+
</code>
</pre>












=== "EU"

    ```sql
    select bigfunctions.eu.parse_date('2021-1-20 ') as cleaned_date

    ```


=== "US"

    ```sql
    select bigfunctions.us.parse_date('2021-1-20 ') as cleaned_date

    ```


=== "europe-west1"

    ```sql
    select bigfunctions.europe_west1.parse_date('2021-1-20 ') as cleaned_date

    ```


=== "your-region2"

    ```sql
    select bigfunctions.your_region2.parse_date('2021-1-20 ') as cleaned_date

    ```





<pre style="margin-top: -1rem;">
<code style="padding-top: 0px; padding-bottom: 0px;">+--------------------+
| cleaned_date       |
+--------------------+
| date('2021-01-20') |
+--------------------+
</code>
</pre>












=== "EU"

    ```sql
    select bigfunctions.eu.parse_date('2021/01/20 ') as cleaned_date

    ```


=== "US"

    ```sql
    select bigfunctions.us.parse_date('2021/01/20 ') as cleaned_date

    ```


=== "europe-west1"

    ```sql
    select bigfunctions.europe_west1.parse_date('2021/01/20 ') as cleaned_date

    ```


=== "your-region2"

    ```sql
    select bigfunctions.your_region2.parse_date('2021/01/20 ') as cleaned_date

    ```





<pre style="margin-top: -1rem;">
<code style="padding-top: 0px; padding-bottom: 0px;">+--------------------+
| cleaned_date       |
+--------------------+
| date('2021-01-20') |
+--------------------+
</code>
</pre>












=== "EU"

    ```sql
    select bigfunctions.eu.parse_date('2021/1/20 ') as cleaned_date

    ```


=== "US"

    ```sql
    select bigfunctions.us.parse_date('2021/1/20 ') as cleaned_date

    ```


=== "europe-west1"

    ```sql
    select bigfunctions.europe_west1.parse_date('2021/1/20 ') as cleaned_date

    ```


=== "your-region2"

    ```sql
    select bigfunctions.your_region2.parse_date('2021/1/20 ') as cleaned_date

    ```





<pre style="margin-top: -1rem;">
<code style="padding-top: 0px; padding-bottom: 0px;">+--------------------+
| cleaned_date       |
+--------------------+
| date('2021-01-20') |
+--------------------+
</code>
</pre>












=== "EU"

    ```sql
    select bigfunctions.eu.parse_date('01/20/21') as cleaned_date

    ```


=== "US"

    ```sql
    select bigfunctions.us.parse_date('01/20/21') as cleaned_date

    ```


=== "europe-west1"

    ```sql
    select bigfunctions.europe_west1.parse_date('01/20/21') as cleaned_date

    ```


=== "your-region2"

    ```sql
    select bigfunctions.your_region2.parse_date('01/20/21') as cleaned_date

    ```





<pre style="margin-top: -1rem;">
<code style="padding-top: 0px; padding-bottom: 0px;">+--------------------+
| cleaned_date       |
+--------------------+
| date('2021-01-20') |
+--------------------+
</code>
</pre>












=== "EU"

    ```sql
    select bigfunctions.eu.parse_date('1/20/21') as cleaned_date

    ```


=== "US"

    ```sql
    select bigfunctions.us.parse_date('1/20/21') as cleaned_date

    ```


=== "europe-west1"

    ```sql
    select bigfunctions.europe_west1.parse_date('1/20/21') as cleaned_date

    ```


=== "your-region2"

    ```sql
    select bigfunctions.your_region2.parse_date('1/20/21') as cleaned_date

    ```





<pre style="margin-top: -1rem;">
<code style="padding-top: 0px; padding-bottom: 0px;">+--------------------+
| cleaned_date       |
+--------------------+
| date('2021-01-20') |
+--------------------+
</code>
</pre>












=== "EU"

    ```sql
    select bigfunctions.eu.parse_date('Wed Jan 20 21:47:00 2021') as cleaned_date

    ```


=== "US"

    ```sql
    select bigfunctions.us.parse_date('Wed Jan 20 21:47:00 2021') as cleaned_date

    ```


=== "europe-west1"

    ```sql
    select bigfunctions.europe_west1.parse_date('Wed Jan 20 21:47:00 2021') as cleaned_date

    ```


=== "your-region2"

    ```sql
    select bigfunctions.your_region2.parse_date('Wed Jan 20 21:47:00 2021') as cleaned_date

    ```





<pre style="margin-top: -1rem;">
<code style="padding-top: 0px; padding-bottom: 0px;">+--------------------+
| cleaned_date       |
+--------------------+
| date('2021-01-20') |
+--------------------+
</code>
</pre>










---









<div style="margin-top: 6rem;"></div>


## <span style="color: var(--md-primary-fg-color);">{...}</span> Transform json

!!! note ""
    **BigQuery json made easy **

    Be amazed with your new SQL powers.

---



### json_items
<div style="position: relative; top: -2rem; margin-bottom:  -2rem; text-align: right; z-index: 9999;">
  
  <a href="https://www.linkedin.com/company/esmoz/" title="Author: Sid Ali" target="_blank">
    <img src="https://media-exp1.licdn.com/dms/image/C560BAQHFcSF8X1MqrQ/company-logo_200_200/0/1636992707472?e=1678320000&v=beta&t=BJmNI_Nd0GuC9Mn3wKc1xGUEpZsCy-CsrTZh47cPcOQ" width="32" style=" border-radius: 50% !important">
  </a>
  
  <a href="https://github.com/unytics/bigfunctions/blob/main/bigfunctions/json_items.yaml" title="Edit on GitHub" target="_blank"><svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24"><path fill="#5d6cc0" d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg></a></div>
```
json_items(json_string)
```

**Description**

Extract `items` from `json_string`
which has only flat (no nested) key-values.
Return `items` as an `array<struct<key string, value string>>`


**Examples**






=== "EU"

    ```sql
    select bigfunctions.eu.json_items('{"created_at": "2022-01-01", "user": "sidali"}') as items

    ```


=== "US"

    ```sql
    select bigfunctions.us.json_items('{"created_at": "2022-01-01", "user": "sidali"}') as items

    ```


=== "europe-west1"

    ```sql
    select bigfunctions.europe_west1.json_items('{"created_at": "2022-01-01", "user": "sidali"}') as items

    ```


=== "your-region2"

    ```sql
    select bigfunctions.your_region2.json_items('{"created_at": "2022-01-01", "user": "sidali"}') as items

    ```





<pre style="margin-top: -1rem;">
<code style="padding-top: 0px; padding-bottom: 0px;">+-----------------------------------------------------------------------------------------------------+
| items                                                                                               |
+-----------------------------------------------------------------------------------------------------+
| [
|   struct("created_at" as key, "date" as value),
|   struct("user" as key, "name" as value)
| ]
 |
+-----------------------------------------------------------------------------------------------------+
</code>
</pre>










---




### json_keys
<div style="position: relative; top: -2rem; margin-bottom:  -2rem; text-align: right; z-index: 9999;">
  
  <a href="https://www.linkedin.com/company/esmoz/" title="Author: Sid Ali" target="_blank">
    <img src="https://media-exp1.licdn.com/dms/image/C560BAQHFcSF8X1MqrQ/company-logo_200_200/0/1636992707472?e=1678320000&v=beta&t=BJmNI_Nd0GuC9Mn3wKc1xGUEpZsCy-CsrTZh47cPcOQ" width="32" style=" border-radius: 50% !important">
  </a>
  
  <a href="https://github.com/unytics/bigfunctions/blob/main/bigfunctions/json_keys.yaml" title="Edit on GitHub" target="_blank"><svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24"><path fill="#5d6cc0" d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg></a></div>
```
json_keys(json_string)
```

**Description**

Extract `keys` from `json_string`
which has only flat (no nested) key-values.
Return `keys` as an `array<string>`


**Examples**






=== "EU"

    ```sql
    select bigfunctions.eu.json_keys('{"created_at": "2022-01-01", "user": "sidali"}') as keys

    ```


=== "US"

    ```sql
    select bigfunctions.us.json_keys('{"created_at": "2022-01-01", "user": "sidali"}') as keys

    ```


=== "europe-west1"

    ```sql
    select bigfunctions.europe_west1.json_keys('{"created_at": "2022-01-01", "user": "sidali"}') as keys

    ```


=== "your-region2"

    ```sql
    select bigfunctions.your_region2.json_keys('{"created_at": "2022-01-01", "user": "sidali"}') as keys

    ```





<pre style="margin-top: -1rem;">
<code style="padding-top: 0px; padding-bottom: 0px;">+------------------------+
| keys                   |
+------------------------+
| ['created_at', 'user'] |
+------------------------+
</code>
</pre>










---




### json_merge
<div style="position: relative; top: -2rem; margin-bottom:  -2rem; text-align: right; z-index: 9999;">
  
  <a href="https://www.linkedin.com/company/esmoz/" title="Author: Thomas Lépine" target="_blank">
    <img src="https://media-exp1.licdn.com/dms/image/C560BAQHFcSF8X1MqrQ/company-logo_200_200/0/1636992707472?e=1678320000&v=beta&t=BJmNI_Nd0GuC9Mn3wKc1xGUEpZsCy-CsrTZh47cPcOQ" width="32" style=" border-radius: 50% !important">
  </a>
  
  <a href="https://github.com/unytics/bigfunctions/blob/main/bigfunctions/json_merge.yaml" title="Edit on GitHub" target="_blank"><svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24"><path fill="#5d6cc0" d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg></a></div>
```
json_merge(json_string1, json_string2)
```

**Description**

Merge `json_string1` and `json_string2`

**Examples**






=== "EU"

    ```sql
    select bigfunctions.eu.json_merge('{"k1": "v1"}', '{"k2": "v2"}') as merged_json

    ```


=== "US"

    ```sql
    select bigfunctions.us.json_merge('{"k1": "v1"}', '{"k2": "v2"}') as merged_json

    ```


=== "europe-west1"

    ```sql
    select bigfunctions.europe_west1.json_merge('{"k1": "v1"}', '{"k2": "v2"}') as merged_json

    ```


=== "your-region2"

    ```sql
    select bigfunctions.your_region2.json_merge('{"k1": "v1"}', '{"k2": "v2"}') as merged_json

    ```





<pre style="margin-top: -1rem;">
<code style="padding-top: 0px; padding-bottom: 0px;">+----------------------------+
| merged_json                |
+----------------------------+
| '{"k1": "v1", "k2": "v2"}' |
+----------------------------+
</code>
</pre>










---




### json_query
<div style="position: relative; top: -2rem; margin-bottom:  -2rem; text-align: right; z-index: 9999;">
  
  <a href="https://www.linkedin.com/company/esmoz/" title="Author: Sid Ali" target="_blank">
    <img src="https://media-exp1.licdn.com/dms/image/C560BAQHFcSF8X1MqrQ/company-logo_200_200/0/1636992707472?e=1678320000&v=beta&t=BJmNI_Nd0GuC9Mn3wKc1xGUEpZsCy-CsrTZh47cPcOQ" width="32" style=" border-radius: 50% !important">
  </a>
  
  <a href="https://github.com/unytics/bigfunctions/blob/main/bigfunctions/json_query.yaml" title="Edit on GitHub" target="_blank"><svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24"><path fill="#5d6cc0" d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg></a></div>
```
json_query(json_string, query)
```

**Description**

Extract data from `json_string` using advanced json querying
offered by [jmespath](https://jmespath.org/).

> *JMESPath Links:*
>
> - See [JMESPath Tutorial](https://jmespath.org/tutorial.html) for exhaustive `query` possibilities
> - [GitHub of jmespath.js](https://github.com/jmespath/jmespath.js)


**Examples**



<span style="color: var(--md-typeset-a-color);">1. Basic Query</span>


=== "EU"

    ```sql
    select bigfunctions.eu.json_query('{"foo": [{"first": "a"}, {"first": "c"}]}', 'foo') as result

    ```


=== "US"

    ```sql
    select bigfunctions.us.json_query('{"foo": [{"first": "a"}, {"first": "c"}]}', 'foo') as result

    ```


=== "europe-west1"

    ```sql
    select bigfunctions.europe_west1.json_query('{"foo": [{"first": "a"}, {"first": "c"}]}', 'foo') as result

    ```


=== "your-region2"

    ```sql
    select bigfunctions.your_region2.json_query('{"foo": [{"first": "a"}, {"first": "c"}]}', 'foo') as result

    ```





<pre style="margin-top: -1rem;">
<code style="padding-top: 0px; padding-bottom: 0px;">+----------------------------------+
| result                           |
+----------------------------------+
| [{"first": "a"}, {"first": "c"}] |
+----------------------------------+
</code>
</pre>









<span style="color: var(--md-typeset-a-color);">2. Getting array sub-items</span>


=== "EU"

    ```sql
    select bigfunctions.eu.json_query('{"foo": [{"first": "a"}, {"first": "c"}]}', 'foo[*].first') as result

    ```


=== "US"

    ```sql
    select bigfunctions.us.json_query('{"foo": [{"first": "a"}, {"first": "c"}]}', 'foo[*].first') as result

    ```


=== "europe-west1"

    ```sql
    select bigfunctions.europe_west1.json_query('{"foo": [{"first": "a"}, {"first": "c"}]}', 'foo[*].first') as result

    ```


=== "your-region2"

    ```sql
    select bigfunctions.your_region2.json_query('{"foo": [{"first": "a"}, {"first": "c"}]}', 'foo[*].first') as result

    ```





<pre style="margin-top: -1rem;">
<code style="padding-top: 0px; padding-bottom: 0px;">+------------+
| result     |
+------------+
| ['a', 'c'] |
+------------+
</code>
</pre>









<span style="color: var(--md-typeset-a-color);">3. Slicing</span>


=== "EU"

    ```sql
    select bigfunctions.eu.json_query('{"foo": [{"first": "a"}, {"first": "c"}]}', 'foo[:1].first') as result

    ```


=== "US"

    ```sql
    select bigfunctions.us.json_query('{"foo": [{"first": "a"}, {"first": "c"}]}', 'foo[:1].first') as result

    ```


=== "europe-west1"

    ```sql
    select bigfunctions.europe_west1.json_query('{"foo": [{"first": "a"}, {"first": "c"}]}', 'foo[:1].first') as result

    ```


=== "your-region2"

    ```sql
    select bigfunctions.your_region2.json_query('{"foo": [{"first": "a"}, {"first": "c"}]}', 'foo[:1].first') as result

    ```





<pre style="margin-top: -1rem;">
<code style="padding-top: 0px; padding-bottom: 0px;">+--------+
| result |
+--------+
| ['a']  |
+--------+
</code>
</pre>









<span style="color: var(--md-typeset-a-color);">4. Projecting</span>


=== "EU"

    ```sql
    select bigfunctions.eu.json_query('{"foo": [{"first": "a"}, {"first": "c"}]}', 'foo[*].{name: first}') as result

    ```


=== "US"

    ```sql
    select bigfunctions.us.json_query('{"foo": [{"first": "a"}, {"first": "c"}]}', 'foo[*].{name: first}') as result

    ```


=== "europe-west1"

    ```sql
    select bigfunctions.europe_west1.json_query('{"foo": [{"first": "a"}, {"first": "c"}]}', 'foo[*].{name: first}') as result

    ```


=== "your-region2"

    ```sql
    select bigfunctions.your_region2.json_query('{"foo": [{"first": "a"}, {"first": "c"}]}', 'foo[*].{name: first}') as result

    ```





<pre style="margin-top: -1rem;">
<code style="padding-top: 0px; padding-bottom: 0px;">+--------------------------------+
| result                         |
+--------------------------------+
| [{"name": "a"}, {"name": "c"}] |
+--------------------------------+
</code>
</pre>










---




### json_schema
<div style="position: relative; top: -2rem; margin-bottom:  -2rem; text-align: right; z-index: 9999;">
  
  <a href="https://www.linkedin.com/in/paul-marcombes" title="Author: Paul Marcombes" target="_blank">
    <img src="https://media-exp1.licdn.com/dms/image/C4E03AQF92ENRMYC3Mw/profile-displayphoto-shrink_800_800/0/1656924490995?e=1675900800&v=beta&t=Ertn0DSUvqzexmymI6NDba3TrXaSLRM_cQ5dxjmTkzo" width="32" style=" border-radius: 50% !important">
  </a>
  
  <a href="https://github.com/unytics/bigfunctions/blob/main/bigfunctions/json_schema.yaml" title="Edit on GitHub" target="_blank"><svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24"><path fill="#5d6cc0" d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg></a></div>
```
json_schema(json_string)
```

**Description**

Return the schema of a json string as `[{path, type}]`
with `path` the path of the nested field
and `type` among (`string`, `numeric`, `bool`, `date`, `timestamp`)


**Examples**






=== "EU"

    ```sql
    select bigfunctions.eu.json_schema('{"created_at": "2022-01-01", "user": {"name": "James", "friends": ["Jack", "Peter"]}}') as schema

    ```


=== "US"

    ```sql
    select bigfunctions.us.json_schema('{"created_at": "2022-01-01", "user": {"name": "James", "friends": ["Jack", "Peter"]}}') as schema

    ```


=== "europe-west1"

    ```sql
    select bigfunctions.europe_west1.json_schema('{"created_at": "2022-01-01", "user": {"name": "James", "friends": ["Jack", "Peter"]}}') as schema

    ```


=== "your-region2"

    ```sql
    select bigfunctions.your_region2.json_schema('{"created_at": "2022-01-01", "user": {"name": "James", "friends": ["Jack", "Peter"]}}') as schema

    ```





<pre style="margin-top: -1rem;">
<code style="padding-top: 0px; padding-bottom: 0px;">+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
| schema                                                                                                                                                          |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
| [
|   struct("created_at" as path, "date" as type),
|   struct("user.name" as path, "string" as type),
|   struct("user.friends" as path, "array" as type)
| ]
 |
+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
</code>
</pre>










---




### json_values
<div style="position: relative; top: -2rem; margin-bottom:  -2rem; text-align: right; z-index: 9999;">
  
  <a href="https://www.linkedin.com/company/esmoz/" title="Author: Sid Ali" target="_blank">
    <img src="https://media-exp1.licdn.com/dms/image/C560BAQHFcSF8X1MqrQ/company-logo_200_200/0/1636992707472?e=1678320000&v=beta&t=BJmNI_Nd0GuC9Mn3wKc1xGUEpZsCy-CsrTZh47cPcOQ" width="32" style=" border-radius: 50% !important">
  </a>
  
  <a href="https://github.com/unytics/bigfunctions/blob/main/bigfunctions/json_values.yaml" title="Edit on GitHub" target="_blank"><svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24"><path fill="#5d6cc0" d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg></a></div>
```
json_values(json_string)
```

**Description**

Extract `values` from `json_string`
which has only flat (no nested) key-values.
Return `values` as an `array<string>`


**Examples**






=== "EU"

    ```sql
    select bigfunctions.eu.json_values('{"created_at": "2022-01-01", "user": "sidali"}') as values

    ```


=== "US"

    ```sql
    select bigfunctions.us.json_values('{"created_at": "2022-01-01", "user": "sidali"}') as values

    ```


=== "europe-west1"

    ```sql
    select bigfunctions.europe_west1.json_values('{"created_at": "2022-01-01", "user": "sidali"}') as values

    ```


=== "your-region2"

    ```sql
    select bigfunctions.your_region2.json_values('{"created_at": "2022-01-01", "user": "sidali"}') as values

    ```





<pre style="margin-top: -1rem;">
<code style="padding-top: 0px; padding-bottom: 0px;">+--------------------------+
| values                   |
+--------------------------+
| ['2022-01-01', 'sidali'] |
+--------------------------+
</code>
</pre>










---









<div style="margin-top: 6rem;"></div>


## <span style="color: var(--md-primary-fg-color);">[...]</span> Transform array

!!! note ""
    **BigQuery arrays made easy **

    Be amazed with your new SQL powers.

---



### are_arrays_equal
<div style="position: relative; top: -2rem; margin-bottom:  -2rem; text-align: right; z-index: 9999;">
  
  <a href="https://www.linkedin.com/company/esmoz/" title="Author: Sid Ali" target="_blank">
    <img src="https://media-exp1.licdn.com/dms/image/C560BAQHFcSF8X1MqrQ/company-logo_200_200/0/1636992707472?e=1678320000&v=beta&t=BJmNI_Nd0GuC9Mn3wKc1xGUEpZsCy-CsrTZh47cPcOQ" width="32" style=" border-radius: 50% !important">
  </a>
  
  <a href="https://github.com/unytics/bigfunctions/blob/main/bigfunctions/are_arrays_equal.yaml" title="Edit on GitHub" target="_blank"><svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24"><path fill="#5d6cc0" d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg></a></div>
```
are_arrays_equal(array1, array2)
```

**Description**

Return true if `array1` = `array2`
and false otherwise


**Examples**






=== "EU"

    ```sql
    select bigfunctions.eu.are_arrays_equal([1, 4, 3], [1, 4, 3]) as are_arrays_equal

    ```


=== "US"

    ```sql
    select bigfunctions.us.are_arrays_equal([1, 4, 3], [1, 4, 3]) as are_arrays_equal

    ```


=== "europe-west1"

    ```sql
    select bigfunctions.europe_west1.are_arrays_equal([1, 4, 3], [1, 4, 3]) as are_arrays_equal

    ```


=== "your-region2"

    ```sql
    select bigfunctions.your_region2.are_arrays_equal([1, 4, 3], [1, 4, 3]) as are_arrays_equal

    ```





<pre style="margin-top: -1rem;">
<code style="padding-top: 0px; padding-bottom: 0px;">+------------------+
| are_arrays_equal |
+------------------+
| true             |
+------------------+
</code>
</pre>












=== "EU"

    ```sql
    select bigfunctions.eu.are_arrays_equal([1, 4, 3], [1, 4]) as are_arrays_equal

    ```


=== "US"

    ```sql
    select bigfunctions.us.are_arrays_equal([1, 4, 3], [1, 4]) as are_arrays_equal

    ```


=== "europe-west1"

    ```sql
    select bigfunctions.europe_west1.are_arrays_equal([1, 4, 3], [1, 4]) as are_arrays_equal

    ```


=== "your-region2"

    ```sql
    select bigfunctions.your_region2.are_arrays_equal([1, 4, 3], [1, 4]) as are_arrays_equal

    ```





<pre style="margin-top: -1rem;">
<code style="padding-top: 0px; padding-bottom: 0px;">+------------------+
| are_arrays_equal |
+------------------+
| false            |
+------------------+
</code>
</pre>










---




### distinct_values
<div style="position: relative; top: -2rem; margin-bottom:  -2rem; text-align: right; z-index: 9999;">
  
  <a href="https://www.linkedin.com/in/paul-marcombes" title="Author: Paul Marcombes" target="_blank">
    <img src="https://media-exp1.licdn.com/dms/image/C4E03AQF92ENRMYC3Mw/profile-displayphoto-shrink_800_800/0/1656924490995?e=1675900800&v=beta&t=Ertn0DSUvqzexmymI6NDba3TrXaSLRM_cQ5dxjmTkzo" width="32" style=" border-radius: 50% !important">
  </a>
  
  <a href="https://github.com/unytics/bigfunctions/blob/main/bigfunctions/distinct_values.yaml" title="Edit on GitHub" target="_blank"><svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24"><path fill="#5d6cc0" d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg></a></div>
```
distinct_values(arr)
```

**Description**

Return distinct values

**Examples**






=== "EU"

    ```sql
    select bigfunctions.eu.distinct_values([1, 4, 3, 4]) as distinct_values

    ```


=== "US"

    ```sql
    select bigfunctions.us.distinct_values([1, 4, 3, 4]) as distinct_values

    ```


=== "europe-west1"

    ```sql
    select bigfunctions.europe_west1.distinct_values([1, 4, 3, 4]) as distinct_values

    ```


=== "your-region2"

    ```sql
    select bigfunctions.your_region2.distinct_values([1, 4, 3, 4]) as distinct_values

    ```





<pre style="margin-top: -1rem;">
<code style="padding-top: 0px; padding-bottom: 0px;">+-----------------+
| distinct_values |
+-----------------+
| [1, 4, 3]       |
+-----------------+
</code>
</pre>










---




### find_value
<div style="position: relative; top: -2rem; margin-bottom:  -2rem; text-align: right; z-index: 9999;">
  
  <a href="https://www.linkedin.com/company/esmoz/" title="Author: Thomas Lépine" target="_blank">
    <img src="https://media-exp1.licdn.com/dms/image/C560BAQHFcSF8X1MqrQ/company-logo_200_200/0/1636992707472?e=1678320000&v=beta&t=BJmNI_Nd0GuC9Mn3wKc1xGUEpZsCy-CsrTZh47cPcOQ" width="32" style=" border-radius: 50% !important">
  </a>
  
  <a href="https://github.com/unytics/bigfunctions/blob/main/bigfunctions/find_value.yaml" title="Edit on GitHub" target="_blank"><svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24"><path fill="#5d6cc0" d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg></a></div>
```
find_value(arr, value)
```

**Description**

Return the first `offset` (zero-based index) of `value` in array `arr`
(or `null` if `value` is not in `arr`).

**Examples**



<span style="color: var(--md-typeset-a-color);">1. When `value` is in array</span>


=== "EU"

    ```sql
    select bigfunctions.eu.find_value([3, 4], 4) as offset

    ```


=== "US"

    ```sql
    select bigfunctions.us.find_value([3, 4], 4) as offset

    ```


=== "europe-west1"

    ```sql
    select bigfunctions.europe_west1.find_value([3, 4], 4) as offset

    ```


=== "your-region2"

    ```sql
    select bigfunctions.your_region2.find_value([3, 4], 4) as offset

    ```





<pre style="margin-top: -1rem;">
<code style="padding-top: 0px; padding-bottom: 0px;">+--------+
| offset |
+--------+
| 1      |
+--------+
</code>
</pre>









<span style="color: var(--md-typeset-a-color);">2. When `value` is not in array</span>


=== "EU"

    ```sql
    select bigfunctions.eu.find_value([3, 4], 7) as offset

    ```


=== "US"

    ```sql
    select bigfunctions.us.find_value([3, 4], 7) as offset

    ```


=== "europe-west1"

    ```sql
    select bigfunctions.europe_west1.find_value([3, 4], 7) as offset

    ```


=== "your-region2"

    ```sql
    select bigfunctions.your_region2.find_value([3, 4], 7) as offset

    ```





<pre style="margin-top: -1rem;">
<code style="padding-top: 0px; padding-bottom: 0px;">+--------+
| offset |
+--------+
| null   |
+--------+
</code>
</pre>










---




### last_element
<div style="position: relative; top: -2rem; margin-bottom:  -2rem; text-align: right; z-index: 9999;">
  
  <a href="https://www.linkedin.com/in/taylorabrownlow/" title="Credits: Taylor Brownlow" target="_blank">
    <img src="https://media-exp1.licdn.com/dms/image/C4E03AQFCRlj44wnbhA/profile-displayphoto-shrink_200_200/0/1579795128165?e=1672272000&v=beta&t=LxL7tn53S_dQU0jMAeT3lHiAP4anA8GSiYD71u63pMs" width="32" style=" border-radius: 50% !important">
  </a>
  
  <a href="https://github.com/unytics/bigfunctions/blob/main/bigfunctions/last_element.yaml" title="Edit on GitHub" target="_blank"><svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24"><path fill="#5d6cc0" d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg></a></div>
```
last_element(arr)
```

**Description**

Return last element of array
*(inspired from [sql-snippets repo](https://github.com/count/sql-snippets/blob/main/bigquery/get-last-array-element.md))*

**Examples**






=== "EU"

    ```sql
    select bigfunctions.eu.last_element([1, 2, 3]) as element

    ```


=== "US"

    ```sql
    select bigfunctions.us.last_element([1, 2, 3]) as element

    ```


=== "europe-west1"

    ```sql
    select bigfunctions.europe_west1.last_element([1, 2, 3]) as element

    ```


=== "your-region2"

    ```sql
    select bigfunctions.your_region2.last_element([1, 2, 3]) as element

    ```





<pre style="margin-top: -1rem;">
<code style="padding-top: 0px; padding-bottom: 0px;">+---------+
| element |
+---------+
| 3       |
+---------+
</code>
</pre>










---




### max_value
<div style="position: relative; top: -2rem; margin-bottom:  -2rem; text-align: right; z-index: 9999;">
  
  <a href="https://www.linkedin.com/in/taylorabrownlow/" title="Credits: Taylor Brownlow" target="_blank">
    <img src="https://media-exp1.licdn.com/dms/image/C4E03AQFCRlj44wnbhA/profile-displayphoto-shrink_200_200/0/1579795128165?e=1672272000&v=beta&t=LxL7tn53S_dQU0jMAeT3lHiAP4anA8GSiYD71u63pMs" width="32" style=" border-radius: 50% !important">
  </a>
  
  <a href="https://github.com/unytics/bigfunctions/blob/main/bigfunctions/max_value.yaml" title="Edit on GitHub" target="_blank"><svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24"><path fill="#5d6cc0" d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg></a></div>
```
max_value(arr)
```

**Description**

Return max value of array
*(inspired from [sql-snippets repo](https://github.com/count/sql-snippets/blob/main/bigquery/least-array.md))*

**Examples**






=== "EU"

    ```sql
    select bigfunctions.eu.max_value([1, 4, 3]) as value

    ```


=== "US"

    ```sql
    select bigfunctions.us.max_value([1, 4, 3]) as value

    ```


=== "europe-west1"

    ```sql
    select bigfunctions.europe_west1.max_value([1, 4, 3]) as value

    ```


=== "your-region2"

    ```sql
    select bigfunctions.your_region2.max_value([1, 4, 3]) as value

    ```





<pre style="margin-top: -1rem;">
<code style="padding-top: 0px; padding-bottom: 0px;">+-------+
| value |
+-------+
| 4     |
+-------+
</code>
</pre>










---




### median_value
<div style="position: relative; top: -2rem; margin-bottom:  -2rem; text-align: right; z-index: 9999;">
  
  <a href="https://www.linkedin.com/in/taylorabrownlow/" title="Credits: Taylor Brownlow" target="_blank">
    <img src="https://media-exp1.licdn.com/dms/image/C4E03AQFCRlj44wnbhA/profile-displayphoto-shrink_200_200/0/1579795128165?e=1672272000&v=beta&t=LxL7tn53S_dQU0jMAeT3lHiAP4anA8GSiYD71u63pMs" width="32" style=" border-radius: 50% !important">
  </a>
  
  <a href="https://github.com/unytics/bigfunctions/blob/main/bigfunctions/median_value.yaml" title="Edit on GitHub" target="_blank"><svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24"><path fill="#5d6cc0" d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg></a></div>
```
median_value(arr)
```

**Description**

Return median value of array
*(inspired from [sql-snippets repo](https://github.com/count/sql-snippets/blob/main/bigquery/median.md))*

**Examples**



<span style="color: var(--md-typeset-a-color);">1. When array length is odd</span>


=== "EU"

    ```sql
    select bigfunctions.eu.median_value([1, 4, 3]) as value

    ```


=== "US"

    ```sql
    select bigfunctions.us.median_value([1, 4, 3]) as value

    ```


=== "europe-west1"

    ```sql
    select bigfunctions.europe_west1.median_value([1, 4, 3]) as value

    ```


=== "your-region2"

    ```sql
    select bigfunctions.your_region2.median_value([1, 4, 3]) as value

    ```





<pre style="margin-top: -1rem;">
<code style="padding-top: 0px; padding-bottom: 0px;">+-------+
| value |
+-------+
| 3     |
+-------+
</code>
</pre>









<span style="color: var(--md-typeset-a-color);">2. When array length is even</span>


=== "EU"

    ```sql
    select bigfunctions.eu.median_value([1, 4, 3, 2]) as value

    ```


=== "US"

    ```sql
    select bigfunctions.us.median_value([1, 4, 3, 2]) as value

    ```


=== "europe-west1"

    ```sql
    select bigfunctions.europe_west1.median_value([1, 4, 3, 2]) as value

    ```


=== "your-region2"

    ```sql
    select bigfunctions.your_region2.median_value([1, 4, 3, 2]) as value

    ```





<pre style="margin-top: -1rem;">
<code style="padding-top: 0px; padding-bottom: 0px;">+-------+
| value |
+-------+
| 2.5   |
+-------+
</code>
</pre>










---




### min_value
<div style="position: relative; top: -2rem; margin-bottom:  -2rem; text-align: right; z-index: 9999;">
  
  <a href="https://www.linkedin.com/in/taylorabrownlow/" title="Credits: Taylor Brownlow" target="_blank">
    <img src="https://media-exp1.licdn.com/dms/image/C4E03AQFCRlj44wnbhA/profile-displayphoto-shrink_200_200/0/1579795128165?e=1672272000&v=beta&t=LxL7tn53S_dQU0jMAeT3lHiAP4anA8GSiYD71u63pMs" width="32" style=" border-radius: 50% !important">
  </a>
  
  <a href="https://github.com/unytics/bigfunctions/blob/main/bigfunctions/min_value.yaml" title="Edit on GitHub" target="_blank"><svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24"><path fill="#5d6cc0" d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg></a></div>
```
min_value(arr)
```

**Description**

Return min value of array
*(inspired from [sql-snippets repo](https://github.com/count/sql-snippets/blob/main/bigquery/least-array.md))*

**Examples**






=== "EU"

    ```sql
    select bigfunctions.eu.min_value([1, 4, 3]) as value

    ```


=== "US"

    ```sql
    select bigfunctions.us.min_value([1, 4, 3]) as value

    ```


=== "europe-west1"

    ```sql
    select bigfunctions.europe_west1.min_value([1, 4, 3]) as value

    ```


=== "your-region2"

    ```sql
    select bigfunctions.your_region2.min_value([1, 4, 3]) as value

    ```





<pre style="margin-top: -1rem;">
<code style="padding-top: 0px; padding-bottom: 0px;">+-------+
| value |
+-------+
| 1     |
+-------+
</code>
</pre>










---




### remove_value
<div style="position: relative; top: -2rem; margin-bottom:  -2rem; text-align: right; z-index: 9999;">
  
  <a href="https://www.linkedin.com/company/esmoz/" title="Author: Sid Ali" target="_blank">
    <img src="https://media-exp1.licdn.com/dms/image/C560BAQHFcSF8X1MqrQ/company-logo_200_200/0/1636992707472?e=1678320000&v=beta&t=BJmNI_Nd0GuC9Mn3wKc1xGUEpZsCy-CsrTZh47cPcOQ" width="32" style=" border-radius: 50% !important">
  </a>
  
  <a href="https://github.com/unytics/bigfunctions/blob/main/bigfunctions/remove_value.yaml" title="Edit on GitHub" target="_blank"><svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24"><path fill="#5d6cc0" d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg></a></div>
```
remove_value(arr, value)
```

**Description**

Return an array with all values except `value`.

**Examples**






=== "EU"

    ```sql
    select bigfunctions.eu.remove_value([1, 4, 3, 8], 4) as arr

    ```


=== "US"

    ```sql
    select bigfunctions.us.remove_value([1, 4, 3, 8], 4) as arr

    ```


=== "europe-west1"

    ```sql
    select bigfunctions.europe_west1.remove_value([1, 4, 3, 8], 4) as arr

    ```


=== "your-region2"

    ```sql
    select bigfunctions.your_region2.remove_value([1, 4, 3, 8], 4) as arr

    ```





<pre style="margin-top: -1rem;">
<code style="padding-top: 0px; padding-bottom: 0px;">+-----------+
| arr       |
+-----------+
| [1, 3, 8] |
+-----------+
</code>
</pre>










---




### sort_values
<div style="position: relative; top: -2rem; margin-bottom:  -2rem; text-align: right; z-index: 9999;">
  
  <a href="https://www.linkedin.com/in/paul-marcombes" title="Author: Paul Marcombes" target="_blank">
    <img src="https://media-exp1.licdn.com/dms/image/C4E03AQF92ENRMYC3Mw/profile-displayphoto-shrink_800_800/0/1656924490995?e=1675900800&v=beta&t=Ertn0DSUvqzexmymI6NDba3TrXaSLRM_cQ5dxjmTkzo" width="32" style=" border-radius: 50% !important">
  </a>
  
  <a href="https://github.com/unytics/bigfunctions/blob/main/bigfunctions/sort_values.yaml" title="Edit on GitHub" target="_blank"><svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24"><path fill="#5d6cc0" d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg></a></div>
```
sort_values(arr)
```

**Description**

Return sorted array (ascending)

**Examples**






=== "EU"

    ```sql
    select bigfunctions.eu.sort_values([1, 4, 3]) as sorted_array

    ```


=== "US"

    ```sql
    select bigfunctions.us.sort_values([1, 4, 3]) as sorted_array

    ```


=== "europe-west1"

    ```sql
    select bigfunctions.europe_west1.sort_values([1, 4, 3]) as sorted_array

    ```


=== "your-region2"

    ```sql
    select bigfunctions.your_region2.sort_values([1, 4, 3]) as sorted_array

    ```





<pre style="margin-top: -1rem;">
<code style="padding-top: 0px; padding-bottom: 0px;">+--------------+
| sorted_array |
+--------------+
| [1, 3, 4]    |
+--------------+
</code>
</pre>










---




### sort_values_desc
<div style="position: relative; top: -2rem; margin-bottom:  -2rem; text-align: right; z-index: 9999;">
  
  <a href="https://www.linkedin.com/in/paul-marcombes" title="Author: Paul Marcombes" target="_blank">
    <img src="https://media-exp1.licdn.com/dms/image/C4E03AQF92ENRMYC3Mw/profile-displayphoto-shrink_800_800/0/1656924490995?e=1675900800&v=beta&t=Ertn0DSUvqzexmymI6NDba3TrXaSLRM_cQ5dxjmTkzo" width="32" style=" border-radius: 50% !important">
  </a>
  
  <a href="https://github.com/unytics/bigfunctions/blob/main/bigfunctions/sort_values_desc.yaml" title="Edit on GitHub" target="_blank"><svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24"><path fill="#5d6cc0" d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg></a></div>
```
sort_values_desc(arr)
```

**Description**

Return sorted array (descending)

**Examples**






=== "EU"

    ```sql
    select bigfunctions.eu.sort_values_desc([1, 4, 3]) as sorted_array

    ```


=== "US"

    ```sql
    select bigfunctions.us.sort_values_desc([1, 4, 3]) as sorted_array

    ```


=== "europe-west1"

    ```sql
    select bigfunctions.europe_west1.sort_values_desc([1, 4, 3]) as sorted_array

    ```


=== "your-region2"

    ```sql
    select bigfunctions.your_region2.sort_values_desc([1, 4, 3]) as sorted_array

    ```





<pre style="margin-top: -1rem;">
<code style="padding-top: 0px; padding-bottom: 0px;">+--------------+
| sorted_array |
+--------------+
| [4, 3, 1]    |
+--------------+
</code>
</pre>










---




### sum_values
<div style="position: relative; top: -2rem; margin-bottom:  -2rem; text-align: right; z-index: 9999;">
  
  <a href="https://www.linkedin.com/in/benjamin-tabet" title="Author: Benjamin Tabet" target="_blank">
    <img src="https://media-exp1.licdn.com/dms/image/C4D03AQGWnyJdEmZeZw/profile-displayphoto-shrink_400_400/0/1667928305931?e=1673481600&v=beta&t=sxH1fFMPjj9ASbqfQ6TkIpWKk_PQ0hUAhOtuAs2zTu0" width="32" style=" border-radius: 50% !important">
  </a>
  
  <a href="https://github.com/unytics/bigfunctions/blob/main/bigfunctions/sum_values.yaml" title="Edit on GitHub" target="_blank"><svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24"><path fill="#5d6cc0" d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg></a></div>
```
sum_values(arr)
```

**Description**

Return the sum of array values

**Examples**






=== "EU"

    ```sql
    select bigfunctions.eu.sum_values([1, 4, 3]) as value

    ```


=== "US"

    ```sql
    select bigfunctions.us.sum_values([1, 4, 3]) as value

    ```


=== "europe-west1"

    ```sql
    select bigfunctions.europe_west1.sum_values([1, 4, 3]) as value

    ```


=== "your-region2"

    ```sql
    select bigfunctions.your_region2.sum_values([1, 4, 3]) as value

    ```





<pre style="margin-top: -1rem;">
<code style="padding-top: 0px; padding-bottom: 0px;">+-------+
| value |
+-------+
| 8     |
+-------+
</code>
</pre>










---









<div style="margin-top: 6rem;"></div>


## 🌐 Graph

!!! note ""
    **Graph Algorithms **

    No need for neo4j nor spark graphframes --> go BigQuery boosted by BigFunctions!

---



### connected_components
<div style="position: relative; top: -2rem; margin-bottom:  -2rem; text-align: right; z-index: 9999;">
  
  <a href="https://www.linkedin.com/in/furcy-pin-3790b028/" title="Author: Furcy Pin" target="_blank">
    <img src="https://media-exp1.licdn.com/dms/image/C4D03AQFK5YDJyod_3A/profile-displayphoto-shrink_200_200/0/1590431668428?e=1670457600&v=beta&t=f0Fd9bV-sSssoLBQ2R03WgEUvP52gdBLv120z-Q-OGc" width="32" style=" border-radius: 50% !important">
  </a>
  
  <a href="https://github.com/unytics/bigfunctions/blob/main/bigfunctions/connected_components.yaml" title="Edit on GitHub" target="_blank"><svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24"><path fill="#5d6cc0" d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg></a></div>
```
connected_components(fully_qualified_table)
```

**Description**

Compute the connected components of a non-directed graph.

Given a table with two columns of the same type STRING or INTEGER representing the edges of a graph,
this computes a new temporary table called `bigfunction_result` containing two columns of the same type
named `node_id` and `connected_component_id`.

This is an implementation of the Alternating Algorithm (large-star, small-star) described in the 2014 paper
"Connected Components in MapReduce and Beyond" written by {rkiveris, silviol, mirrokni, rvibhor, sergeiv} @google.com

PERFORMANCE AND COST CONSIDERATIONS

- This algorithm has been proved to converge in O(log(n)²) and is conjectured to converge in O(log(n)), where n
is the number of nodes in the graph. It was the most performant known distributed connected component algorithm
last time I checked (in 2017).
- This implementation persists temporary results at each iteration loop: for the BigQuery pricing, you should
be expecting it to cost the equivalent of 15 to 30 scans on your input table. Since the input table has only
two columns, this should be reasonable, and we recommend using INTEGER columns rather than STRING when possible.
- If your graph contains nodes with a very high number of neighbors, the algorithm may crash. It is recommended
to apply a pre-filtering on your nodes and remove nodes with a pathologically high cardinality.
You should also monitor actively the number of nodes filtered this way and their cardinality, as this could help
you detect a data quality deterioration in your input graph.
If the input graph contains duplicate edges, they will be automatically removed by the algorithm.

ISOLATED NODES: If you want to have isolated nodes (nodes that have no neighbors)
in the resulting graph, there is two possible ways to achieve this:

- Add self-loops edges to all your nodes in your input graph (it also works if you add edges between all the graph
   nodes and a fictitious node with id NULL)
- Only add edges between distinct nodes to your input, and perform a join between your input graph and the
   algorithm's output to find all the nodes that have disappeared. These will be the isolated nodes.
   This second method requires a little more work but it should also be cheaper.


**Examples**



<span style="color: var(--md-typeset-a-color);">Identify the two connected components of a graph which has 6 nodes and is represented by the edges below:
```
+---------+-----+
| node1 | node2 |
+-------+-------+
|   1   |   2   |
|   2   |   3   |
|   3   |   4   |
|   5   |   6   |
+-------+-------+
```
</span>


=== "EU"

    ```sql
    call bigfunctions.eu.connected_components('bigfunctions.eu.sample_graph');
    select * from bigfunction_result;
    ```


=== "US"

    ```sql
    call bigfunctions.us.connected_components('bigfunctions.us.sample_graph');
    select * from bigfunction_result;
    ```


=== "europe-west1"

    ```sql
    call bigfunctions.europe_west1.connected_components('bigfunctions.europe_west1.sample_graph');
    select * from bigfunction_result;
    ```


=== "your-region2"

    ```sql
    call bigfunctions.your_region2.connected_components('bigfunctions.your_region2.sample_graph');
    select * from bigfunction_result;
    ```







<pre style="margin-top: -1rem;">
<code style="padding-top: 0px; padding-bottom: 0px;">
+---------+------------------------+
| node_id | connected_component_id |
+---------+------------------------+
|    1    |           1            |
|    2    |           1            |
|    3    |           1            |
|    4    |           1            |
|    5    |           5            |
|    6    |           5            |
+---------+------------------------+

</code>
</pre>








---









<div style="margin-top: 6rem;"></div>


## 💬 Notify

!!! note ""
    **Send infos to your customers, alert the operations teams, send reportings to business **

    Spread the word to the world!

---



### notify_gmail
<div style="position: relative; top: -2rem; margin-bottom:  -2rem; text-align: right; z-index: 9999;">
  
  <a href="https://www.linkedin.com/in/paul-marcombes" title="Author: Paul Marcombes" target="_blank">
    <img src="https://media-exp1.licdn.com/dms/image/C4E03AQF92ENRMYC3Mw/profile-displayphoto-shrink_800_800/0/1656924490995?e=1675900800&v=beta&t=Ertn0DSUvqzexmymI6NDba3TrXaSLRM_cQ5dxjmTkzo" width="32" style=" border-radius: 50% !important">
  </a>
  
  <a href="https://github.com/unytics/bigfunctions/blob/main/bigfunctions/notify_gmail.yaml" title="Edit on GitHub" target="_blank"><svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24"><path fill="#5d6cc0" d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg></a></div>
```
notify_gmail(recipients, subject, body, attachment_filename, attachment_content)
```

**Description**

Send email via gmail

**Examples**



<span style="color: var(--md-typeset-a-color);">1. Send email without file attached</span>


=== "EU"

    ```sql
    select bigfunctions.eu.notify_gmail('contact@unytics.io', 'I love BigFunctions', 'Hey Paul, could you deploy more BigFunctions 🙏?', null, null) as success

    ```


=== "US"

    ```sql
    select bigfunctions.us.notify_gmail('contact@unytics.io', 'I love BigFunctions', 'Hey Paul, could you deploy more BigFunctions 🙏?', null, null) as success

    ```


=== "europe-west1"

    ```sql
    select bigfunctions.europe_west1.notify_gmail('contact@unytics.io', 'I love BigFunctions', 'Hey Paul, could you deploy more BigFunctions 🙏?', null, null) as success

    ```


=== "your-region2"

    ```sql
    select bigfunctions.your_region2.notify_gmail('contact@unytics.io', 'I love BigFunctions', 'Hey Paul, could you deploy more BigFunctions 🙏?', null, null) as success

    ```





<pre style="margin-top: -1rem;">
<code style="padding-top: 0px; padding-bottom: 0px;">+---------+
| success |
+---------+
| true    |
+---------+
</code>
</pre>









<span style="color: var(--md-typeset-a-color);">2. Send email with plain text file attached</span>


=== "EU"

    ```sql
    select bigfunctions.eu.notify_gmail('contact@unytics.io', 'I love BigFunctions', 'Hey Paul, could you deploy more BigFunctions 🙏?', 'report.csv', 'col1,col2\nval1,val2\nval3,val4') as success

    ```


=== "US"

    ```sql
    select bigfunctions.us.notify_gmail('contact@unytics.io', 'I love BigFunctions', 'Hey Paul, could you deploy more BigFunctions 🙏?', 'report.csv', 'col1,col2\nval1,val2\nval3,val4') as success

    ```


=== "europe-west1"

    ```sql
    select bigfunctions.europe_west1.notify_gmail('contact@unytics.io', 'I love BigFunctions', 'Hey Paul, could you deploy more BigFunctions 🙏?', 'report.csv', 'col1,col2\nval1,val2\nval3,val4') as success

    ```


=== "your-region2"

    ```sql
    select bigfunctions.your_region2.notify_gmail('contact@unytics.io', 'I love BigFunctions', 'Hey Paul, could you deploy more BigFunctions 🙏?', 'report.csv', 'col1,col2\nval1,val2\nval3,val4') as success

    ```





<pre style="margin-top: -1rem;">
<code style="padding-top: 0px; padding-bottom: 0px;">+---------+
| success |
+---------+
| true    |
+---------+
</code>
</pre>









<span style="color: var(--md-typeset-a-color);">3. Send email with excel file attached</span>


=== "EU"

    ```sql
    select bigfunctions.eu.notify_gmail('contact@unytics.io', 'I love BigFunctions', 'Hey Paul, could you deploy more BigFunctions 🙏?', 'report.xlsx', (select bigfunctions.eu.dump_to_excel('[{"col1": "val1", "col2": "val2"}, {"col1": "val3", "col2": "val4"}]'))) as success

    ```


=== "US"

    ```sql
    select bigfunctions.us.notify_gmail('contact@unytics.io', 'I love BigFunctions', 'Hey Paul, could you deploy more BigFunctions 🙏?', 'report.xlsx', (select bigfunctions.us.dump_to_excel('[{"col1": "val1", "col2": "val2"}, {"col1": "val3", "col2": "val4"}]'))) as success

    ```


=== "europe-west1"

    ```sql
    select bigfunctions.europe_west1.notify_gmail('contact@unytics.io', 'I love BigFunctions', 'Hey Paul, could you deploy more BigFunctions 🙏?', 'report.xlsx', (select bigfunctions.europe_west1.dump_to_excel('[{"col1": "val1", "col2": "val2"}, {"col1": "val3", "col2": "val4"}]'))) as success

    ```


=== "your-region2"

    ```sql
    select bigfunctions.your_region2.notify_gmail('contact@unytics.io', 'I love BigFunctions', 'Hey Paul, could you deploy more BigFunctions 🙏?', 'report.xlsx', (select bigfunctions.your_region2.dump_to_excel('[{"col1": "val1", "col2": "val2"}, {"col1": "val3", "col2": "val4"}]'))) as success

    ```





<pre style="margin-top: -1rem;">
<code style="padding-top: 0px; padding-bottom: 0px;">+---------+
| success |
+---------+
| true    |
+---------+
</code>
</pre>










---









<div style="margin-top: 6rem;"></div>


## 🚀 Export

!!! note ""
    **Get the data out to the outside world **

    Make BigQuery as the golden source of all your SAAS and for all your usages

---



### export_to_gmail
<div style="position: relative; top: -2rem; margin-bottom:  -2rem; text-align: right; z-index: 9999;">
  
  <a href="https://www.linkedin.com/in/paul-marcombes" title="Author: Paul Marcombes" target="_blank">
    <img src="https://media-exp1.licdn.com/dms/image/C4E03AQF92ENRMYC3Mw/profile-displayphoto-shrink_800_800/0/1656924490995?e=1675900800&v=beta&t=Ertn0DSUvqzexmymI6NDba3TrXaSLRM_cQ5dxjmTkzo" width="32" style=" border-radius: 50% !important">
  </a>
  
  <a href="https://github.com/unytics/bigfunctions/blob/main/bigfunctions/export_to_gmail.yaml" title="Edit on GitHub" target="_blank"><svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24"><path fill="#5d6cc0" d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg></a></div>
```
export_to_gmail(table_or_view_or_query, recipients, email_subject, email_body)
```

**Description**

Send email (via gmail) with data attached as excel file

**Examples**






=== "EU"

    ```sql
    call bigfunctions.eu.export_to_gmail('bigfunctions.samples.natality', 'contact@unytics.io', 'Finance Figures for Today', 'Hey Paul, you fill find the figures in the attached excel file. Enjoy 🔥');

    ```












---









<div style="margin-top: 6rem;"></div>


## 🔨 Utils

!!! note ""
    **Utils BigFunctions **

    

---



### chart
<div style="position: relative; top: -2rem; margin-bottom:  -2rem; text-align: right; z-index: 9999;">
  
  <a href="https://www.linkedin.com/in/paul-marcombes" title="Author: Paul Marcombes" target="_blank">
    <img src="https://media-exp1.licdn.com/dms/image/C4E03AQF92ENRMYC3Mw/profile-displayphoto-shrink_800_800/0/1656924490995?e=1675900800&v=beta&t=Ertn0DSUvqzexmymI6NDba3TrXaSLRM_cQ5dxjmTkzo" width="32" style=" border-radius: 50% !important">
  </a>
  
  <a href="https://github.com/unytics/bigfunctions/blob/main/bigfunctions/chart.yaml" title="Edit on GitHub" target="_blank"><svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24"><path fill="#5d6cc0" d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg></a></div>
```
chart(data, chart_type, ylabel)
```

**Description**

Return html with a chartjs chart

**Examples**






=== "EU"

    ```sql
    select bigfunctions.eu.chart([('2022-08-01', 10000.), ('2022-08-02', 20000.), ('2022-08-03', 40000.), ('2022-08-04', 80000.)], 'bar', 'sales') as html

    ```


=== "US"

    ```sql
    select bigfunctions.us.chart([('2022-08-01', 10000.), ('2022-08-02', 20000.), ('2022-08-03', 40000.), ('2022-08-04', 80000.)], 'bar', 'sales') as html

    ```


=== "europe-west1"

    ```sql
    select bigfunctions.europe_west1.chart([('2022-08-01', 10000.), ('2022-08-02', 20000.), ('2022-08-03', 40000.), ('2022-08-04', 80000.)], 'bar', 'sales') as html

    ```


=== "your-region2"

    ```sql
    select bigfunctions.your_region2.chart([('2022-08-01', 10000.), ('2022-08-02', 20000.), ('2022-08-03', 40000.), ('2022-08-04', 80000.)], 'bar', 'sales') as html

    ```








<a href="../assets/images/chart.png"><img alt="screenshot" src="../assets/images/chart.png" style="border: var(--md-code-bg-color) solid 1rem; margin-top: -1rem; width: 100%"></a>



---




### dump_to_excel
<div style="position: relative; top: -2rem; margin-bottom:  -2rem; text-align: right; z-index: 9999;">
  
  <a href="https://www.linkedin.com/in/paul-marcombes" title="Author: Paul Marcombes" target="_blank">
    <img src="https://media-exp1.licdn.com/dms/image/C4E03AQF92ENRMYC3Mw/profile-displayphoto-shrink_800_800/0/1656924490995?e=1675900800&v=beta&t=Ertn0DSUvqzexmymI6NDba3TrXaSLRM_cQ5dxjmTkzo" width="32" style=" border-radius: 50% !important">
  </a>
  
  <a href="https://github.com/unytics/bigfunctions/blob/main/bigfunctions/dump_to_excel.yaml" title="Edit on GitHub" target="_blank"><svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24"><path fill="#5d6cc0" d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg></a></div>
```
dump_to_excel(data)
```

**Description**

Dump data to excel file returned as base64

**Examples**






=== "EU"

    ```sql
    select bigfunctions.eu.dump_to_excel('[{"col1": "row1", "col2": 1}, {"col1": "row2", "col2": 2}]') as excel_base64

    ```


=== "US"

    ```sql
    select bigfunctions.us.dump_to_excel('[{"col1": "row1", "col2": 1}, {"col1": "row2", "col2": 2}]') as excel_base64

    ```


=== "europe-west1"

    ```sql
    select bigfunctions.europe_west1.dump_to_excel('[{"col1": "row1", "col2": 1}, {"col1": "row2", "col2": 2}]') as excel_base64

    ```


=== "your-region2"

    ```sql
    select bigfunctions.your_region2.dump_to_excel('[{"col1": "row1", "col2": 1}, {"col1": "row2", "col2": 2}]') as excel_base64

    ```





<pre style="margin-top: -1rem;">
<code style="padding-top: 0px; padding-bottom: 0px;">+------------------+
| excel_base64     |
+------------------+
| UEsDBBQAAAAAA... |
+------------------+
</code>
</pre>










---




### get_json_column_schema
<div style="position: relative; top: -2rem; margin-bottom:  -2rem; text-align: right; z-index: 9999;">
  
  <a href="https://www.linkedin.com/in/paul-marcombes" title="Author: Paul Marcombes" target="_blank">
    <img src="https://media-exp1.licdn.com/dms/image/C4E03AQF92ENRMYC3Mw/profile-displayphoto-shrink_800_800/0/1656924490995?e=1675900800&v=beta&t=Ertn0DSUvqzexmymI6NDba3TrXaSLRM_cQ5dxjmTkzo" width="32" style=" border-radius: 50% !important">
  </a>
  
  <a href="https://github.com/unytics/bigfunctions/blob/main/bigfunctions/get_json_column_schema.yaml" title="Edit on GitHub" target="_blank"><svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24"><path fill="#5d6cc0" d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg></a></div>
```
get_json_column_schema(table_or_view_or_query, json_column)
```

**Description**

Return the schema of `json_column` of `table_or_view_or_query` as `[{path, type}]`
with `path` the path of the nested field
and `type` among (`string`, `numeric`, `bool`, `date`, `timestamp`)


**Examples**






=== "EU"

    ```sql
    call bigfunctions.eu.get_json_column_schema('bigfunctions.eu.sample_json', 'data');
    select * from bigfunction_result;
    ```


=== "US"

    ```sql
    call bigfunctions.us.get_json_column_schema('bigfunctions.us.sample_json', 'data');
    select * from bigfunction_result;
    ```


=== "europe-west1"

    ```sql
    call bigfunctions.europe_west1.get_json_column_schema('bigfunctions.europe_west1.sample_json', 'data');
    select * from bigfunction_result;
    ```


=== "your-region2"

    ```sql
    call bigfunctions.your_region2.get_json_column_schema('bigfunctions.your_region2.sample_json', 'data');
    select * from bigfunction_result;
    ```







<pre style="margin-top: -1rem;">
<code style="padding-top: 0px; padding-bottom: 0px;">
+----------------+-------------+
| schema.path    | schema.type |
+----------------+-------------+
| "created_at"   | "date"      |
| "user.name"    | "string"    |
| "user.friends" | "array"     |
+----------------+-------------+

</code>
</pre>








---




### get_table_columns
<div style="position: relative; top: -2rem; margin-bottom:  -2rem; text-align: right; z-index: 9999;">
  
  <a href="https://www.linkedin.com/in/furcy-pin-3790b028/" title="Author: Furcy Pin" target="_blank">
    <img src="https://media-exp1.licdn.com/dms/image/C4D03AQFK5YDJyod_3A/profile-displayphoto-shrink_200_200/0/1590431668428?e=1670457600&v=beta&t=f0Fd9bV-sSssoLBQ2R03WgEUvP52gdBLv120z-Q-OGc" width="32" style=" border-radius: 50% !important">
  </a>
  
  <a href="https://github.com/unytics/bigfunctions/blob/main/bigfunctions/get_table_columns.yaml" title="Edit on GitHub" target="_blank"><svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24"><path fill="#5d6cc0" d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg></a></div>
```
get_table_columns(fully_qualified_table)
```

**Description**

Get the column information of the given table from `INFORMATION_SCHEMA.COLUMNS`
and put them in a temporary table called `bigfunction_result`.


**Examples**



<span style="color: var(--md-typeset-a-color);">call `bigfunctions.eu._get_columns`("bigfunctions.samples.natality");
select column_name, data_type from bigfunction_result ;
</span>


=== "EU"

    ```sql
    call bigfunctions.eu.get_table_columns('bigfunctions.samples.natality');

    ```












---






