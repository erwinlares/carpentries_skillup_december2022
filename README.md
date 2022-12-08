![Preview](img/cv_preview.jpg)]

# My data-driven CV

## What

This is a `RMD` document that renders into a CV document in pdf. 

This document is created using the **`R`** Package `vitae` and was inspired by Brian Jenkins's repo https://github.com/tallguyjenks/CV/blob/master/CV.pdf

## Why

I was looking for ways to reduce the painpoints involved in creating and updating my CV. When a new CV-worthy event occurs, one just needs to add a row in the `Excel` that houses the data. Afterward, reknitting the `RMD` produces an updated version.

## How

This document utilizes **RMarkdown** and is compiled through pandoc. This document uses various other packages with `vitae` such as `here`, `tibble`, `glue`, and `magrittr`. 

Unlike Jenkin's approach, I decided to keep all the data in a single Excel workbook with individual sheets for every section of the CV. The `readxl` package takes care of reading in the data. 

## Notable features

The YAML portion of the `RMarkdown` document controls personal information. It includes some customization to match UW-Madison colors in the section headers.

I included some logic to deal with date formatting. 

The `vitae` package includes various layout options. I used `vitae::awesomecv` but there are additional ones available. Notice the colon colon syntax. 

output: vitae::moderncv
output: vitae::hyndman
output: vitae::awesomecv
output: vitae::twentyseconds
output: vitae::markdowncv

One has complete control over how many sections are included int the CV document. Start a new section with a level 1 header and a descriptive name. Inside that section use `vitae::detailed_entries()` function and passed on the data associated with said entry. 

In addition to `vitae::detailed_entries()`, `vitae` also provides that function `vitae::brief_entries()`. I found that I have little used for `brief_entries()`, but it might be worth checking it out. 

In addition to the formatting logic I included for the dates in the `Experience` and `Education` section, one might want to control how many entries to include for the sections with a large number of events such as my `Administrative Services`. There is a filter statement that is commented out that would include just the most recent 5 years.


# Fromt `vitae` documentation

Arguments
data	
A data.frame or tibble.

what	
The primary value of the entry (such as workplace title or degree).

when	
The time of the entry (such as the period spent in the role).

with	
The company or organisation.

.protect	
When TRUE, inputs to the previous arguments will be protected from being parsed as LaTeX code.

where	
The location of the entry.

why	
Any additional information, to be included as dot points. Multiple dot points can be provided via a list column. Alternatively, if the same what, when, with, and where combinations are found in multiple rows, the why entries of these rows will be combined into a list.