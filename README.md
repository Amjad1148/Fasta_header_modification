## Fasta_header_modification

Modifies the header of the fasta and keeps the gene ID and sequence, removing unwanted text from the fasta header

## The fasta files look like 
```
>GWHPEQUH000071 mRNA=GWHTEQUH000071     Gene=GWHGEQUH000071     Position=GWHEQUH00000001: 1980338-1981358, 1981488-1981675: -   Frame=0 OriID=AMN1A008800.1     OriTrascriptID=AMN1A008800.1    transl_table=1  OriGeneID=AMN1A008800    OriSeqID=A1
MPPRNDKDGGEDITVDLYPFIREYKGGRVERFLRSPFVAATEDPAANRGVATRDVIIDNCTGVSLAARTGALVVSVEYRLAPEHPVPAAYDDAWAALQWVASLSDPWLSSYADPERTFLAGDSAGGNIVYNTAVRAAGRGTNIVDIEGLVIVHPYFWGVDRLSSSETVWDGVAMFTPDFVDRLWPYVTAGQLENDDPWINPLDGDIASLMCRRVLVAVAEKDSLSGRGRRLAASMRNLMWADDQ
HAVTLVESEAEDHGFHLYNPMRATSKTLMESIIQFINQRPALPLPAAFPPERHELHLHACQGKDQTSYSAVQPILGVPTRPYVDVFGYGVAMKDSSGPKNTTRTSCLQIGGHERRSSPRTRRYGLSLGHPITSNMRFPLSATTSPGGGCVHFHKFMTI
```
## Running code in Linux 
```
awk '/^>/ {if (match($0, /OriGeneID=([^ ]+)/, a)) print ">" a[1]; else print} !/^>/ {print}' input.fasta > output.fasta
```
# Output after running the above code

```
>AMN1A008800    OriSeqID=A1
MPPRNDKDGGEDITVDLYPFIREYKGGRVERFLRSPFVAATEDPAANRGVATRDVIIDNCTGVSLAARTGALVVSVEYRLAPEHPVPAAYDDAWAALQWVASLSDPWLSSYADPERTFLAGDSAGGNIVYNTAVRAAGRGTNIVDIEGLVIVHPYFWGVDRLSSSETVWDGVAMFTPDFVDRLWPYVTAGQLENDDPWINPLDGDIASLMCRRVLVAVAEKDSLSGRGRRLAASMRNLMWADDQHA
VTLVESEAEDHGFHLYNPMRATSKTLMESIIQFINQRPALPLPAAFPPERHELHLHACQGKDQTSYSAVQPILGVPTRPYVDVFGYGVAMKDSSGPKNTTRTSCLQIGGHERRSSPRTRRYGLSLGHPITSNMRFPLSATTSPGGGCVHFHKFMTI
```
