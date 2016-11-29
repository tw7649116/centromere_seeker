# centromere_seeker
bash script to search for centromeric repeat patterns in long sequence data, using several current tools (trf and R)

#centromere_seeker
#version 2.0 -- 161121

#this script looks for long repeats in pacbio data with trf
#and plots them visually to isolate potential centromeric
#repeats

#must have both tandem repeat finder (trf, https://tandem.bu.edu/trf/trf.html)
#and R (https://www.r-project.org/) installed

#centromere seeker has 2 stages and 2 outputs
#
#stage 1 - determines underlying repeat patterns in the sequencing data
#			this stage runs trf, then converts that data to csv and plots
#			the resulting data in R. the R plot output is "cent_seek_graph.pdf"
#			on screen output will inform you when this has been created, and
#			once it has, you should assess it for patterns that are consistent
#			with a broadly present centromere-sized repeat (see 
#			example_cent_seek_graph.pdf). if you observe a pattern input the
#			centromere size that pattern indicates into the terminal prompt to
#			enter stage 2
#
#stage 2 - the program now switches and gathers the sequence data with pattern
#			lengths that match your hypotesized centromere size (n, 2n, and 4n)
#			there are two outputs:
#
#			centromere_pattern_length_matches.fasta	- includes the n-length 
#														pattern that trf found
#
#			centromere_full_length_matches.fasta	- includes the full match
#														that trf found, which 
#														may include slight 
#														variations in the 
#														pattern
#
#with these fasta outputs, use your favorite alignment program (e.g. AliView)
#to determine if there is a large and common connection across these patterns. 
#if so, that repeat may be very common in the genome of interest which may be 
#indicative of a centromeric repeat.


#cent_seeker_v2.0.sh
#implemented
#	-the ability to pass flags into the program
#	-broke the program into parts that can be run separately