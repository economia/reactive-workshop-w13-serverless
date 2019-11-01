#Typescript in lambda

We can easily write lambdas in typescript thanks to webpack plugin.
Add webpack rule:
```json
module: {
		rules: [
			{
				test: /\.tsx?$/,
				loader: 'ts-loader',
				options: {
					transpileOnly: true
				}
			}
		]
	}
```
Add tsconfig.json

```json
{
	"compilerOptions": {
		"lib": ["es2017"],
		"moduleResolution": "node",
		"sourceMap": true,
		"target": "es2017",
		"resolveJsonModule": true,
		"module": "commonjs",
		"experimentalDecorators": true
	},
	"exclude": ["node_modules"]
}
```
Task:
* rewrite lambda any lambda function to typescript
(we will need to install `tsc` `@types/aws-lambda` `@types/aws-sdk`... )
```typescript
import { Handler, Context } from 'aws-lambda';
export const helloworld: Handler<{}, Context> = async (event, context): Promise<any> => {
    
}
```
