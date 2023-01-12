### .github/workflows/index.yml
```
name: setup-and-test
on: push
jobs: 
	build: 
		runs-on: ubuntu-latest 
		steps: 
			- uses: actions/checkout@v2 
			- uses: actions/setup-node@v2 
				with: 
					node-version: '16.x' 
					cache: npm - перенос зависимостей
			- run: make setup 
			- run: make test 
			- run: make lint
```
