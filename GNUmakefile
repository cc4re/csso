.PHONY: test web shared node

node:
	@make shared
	@cat src/parser.node.js >> .parser.js
	@mv .parser.js lib/parser.js
	@cat src/compressor.node.js >> .compressor.js
	@mv .compressor.js lib/compressor.js
	@cat src/util.node.js >> .util.js
	@mv .util.js lib/util.js
	@cat src/translator.node.js >> .translator.js
	@mv .translator.js lib/translator.js

shared:
	@pecode src/csso.pecode > .parser.js
	@cat src/csso.other.js >> .parser.js
	@cat src/trbl.js > .compressor.js
	@cat src/compressor.shared.js >> .compressor.js
	@cat src/util.shared.js > .util.js
	@cat src/translator.shared.js > .translator.js

test:
	@node test/test.js

web:
	@make shared
	@cat .util.js > web/csso.web.js
	@rm .util.js
	@cat .parser.js >> web/csso.web.js
	@rm .parser.js
	@cat src/compressor.web.js >> web/csso.web.js
	@cat .compressor.js >> web/csso.web.js
	@rm .compressor.js
	@cat .translator.js >> web/csso.web.js
	@rm .translator.js
