# SNVs: Illumina vs ONT

**Author**: Katarina Braun 

## Overview

This script cleans the VCF files generated by the `Illumina Sniffles`  and the `ONT SISPA` pipeline and generates "SNV correlation plots" to compare ONT and Illumina SNVs. 

## Dependencies 
- pandas
- numpy
- matplotlib
- glob
- os
- functools
- pandas
- itertools
- glob
- os
- sklearn 
 
**Visualize**: 
One scatterplot per gene where: 
- x Illumina SNV FREQ 
- y ONT SNV FREQ 
- datapoints are plotted as closed if nonsynonymous and open if synonymous

### a note about numbering schemes 

Everything was mapped to the Madison, WI case reference sequence: MT039887

The numbering schemes in input VCFs differs between the Illumina and ONT files. 
1. **Illumina**: starts from 1 at the beginning of each ORF. 
2. **ONT**: starts from 1 at the beginning of the reference file and increases sequentially through the entire genome. Some of the code below will adjust the numbering scheme in the ONT files to match the Illumina files -- but just make sure you are aware of this if you are looking at the upstream VCF files. 

## Input: 

1. SNV files in VCF format (output from `Sniffles`):
    - `Illumina-Sniffles VCFs`
    
2. SNV files in VCF format (output from the ONT pipeline):
    - `ONT-SISPA VCFs` 

## Output: 

1. Cleaned generated from VCF input files.     

2. Spliced data by sample ID, gene, and synonymous vs nonsynonymous.

3. A PDF version of SNV figures. 
    