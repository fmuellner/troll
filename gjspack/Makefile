
.PHONY: build test test-ci clean demo

build:
	./bin/gjspack --appid=gjspack src/cli.js bin/

test: build
	./bin/gjspack --appid=gjspack-test test/gjspack.test.js test/build/
	test/build/gjspack-test

ci: clean test
	./bin/gjspack --appid=gjspack-demo ./demo/main.js ./demo/build
	cd demo && flatpak-builder --user --force-clean flatpak flatpak.json

clean:
	rm -rf demo/.flatpak-builder demo/flatpak demo/build test/build

demo: build
	./bin/gjspack --appid=gjspack-demo ./demo/main.js ./demo/build
	./demo/build/gjspack-demo
