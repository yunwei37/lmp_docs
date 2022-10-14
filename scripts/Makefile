# test with the files in eunomia-bpf
TEST_CASES_DIRS=$(shell ls -l eunomia-bpf/examples/bpftools | grep ^d | awk '{print $$9}')
.PHONY: test
test:
	rm -rf eunomia-bpf/
	git clone https://github.com/eunomia-bpf/eunomia-bpf --depth 1
	$(MAKE) $(TEST_CASES_DIRS)

$(TEST_CASES_DIRS):
	echo $@
	cp -f eunomia-bpf/examples/bpftools/$@/README.md ../_posts/2020-01-01-$@.md
	cat ../_posts/2020-01-01-$@.md | grep "summary:" | head -1 | sed 's/^summary://' | xargs -I{} sed -i '10 i > {}\n' ../_posts/2020-01-01-$@.md
	sed -i '12 i **Run eBPF program in a line**\n' ../_posts/2020-01-01-$@.md
	sed -i '14 i ```sh' ../_posts/2020-01-01-$@.md
	sed -i '15 i sudo ecli run $@' ../_posts/2020-01-01-$@.md
	sed -i '16 i ```' ../_posts/2020-01-01-$@.md