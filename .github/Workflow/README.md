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
    - uses: actions/checkout@v3
    
    - name: Set Up MS Build
      uses: microsoft/setup-msbuild@v1
      
    - name: Restore dependencies
      run: nuget restore Solution.sln
      
    - name: Build Solution
      run: msbuild Solution.sln 
    
    - name: Creating Zip
      run: zip -r release.zip . -x ".git/*" ".github/*"