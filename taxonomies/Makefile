# Pattern rule to build taxonomies, see https://www.gnu.org/software/make/manual/html_node/Pattern-Intro.html#Pattern-Intro
# this is meant to be run inside the docker container, see build_taxonomies
%.result.txt: %.txt
	perl -CS -Ilib ../scripts/build_tags_taxonomy.pl $* 1
	touch $@

taxonomies: $(wildcard *.result.txt)

all_taxonomies: _reset_taxonomies taxonomies

_reset_taxonomies:
# touch taxonomies sources, then launch build
	for f in *.txt; do if [[ ! "$$f" =~ "result" ]]; then touch  $$f; fi; done


.DEFAULT_GOAL := taxonomies
SHELL := /bin/bash

