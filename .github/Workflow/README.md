name: .NET    
on:
  push:
    branches: [ "main" ]
  pull_request:
    branches: [ "main" ]

jobs:
  build:

    runs-on: [windows-latest]

    steps:
    - uses: actions/badshasorder10@gmail.com
    
    - name: Set Up MS Build
      uses: microsoft/badshasorder10@gmail.com
      
    - name: Restore dependencies
      run: nuget restore Solution.sln
      
    - name: Build Solution
      run: msbuild Solution.sln 
    
    - name: Creating Zip
      run: zip -r release.zip . -x ".git/*" ".github/*"
