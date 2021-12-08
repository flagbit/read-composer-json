# read-composer-json

This action gives you access to the composer.json file content in form of environment variables.

## Minimum example

``` yaml
    - name: "Read Composer file"
      id: "composer"
      uses:  "flagbit/read-composer-json@v1.0.0"
    - name: "Get composer package name"
      run: "echo ${{ env.composer_name }}"
```

## Access packages

Because composer packages contain slashes or backslashes in keys, they are not a valid env-name. In this case both
will be replaced with dashes. For example:

``` yaml
    - name: "Get Symfony package version constraint"
      run: "echo ${{ env.composer_require_symfony-symfony }}"
```

## Composer file path

In case you have your composer file in a different path than the project's root directory, you can set a path name
to the correct composer path.

``` yaml
    - name: "Read Composer file"
      id: "composer"
      uses:  "flagbit/read-composer-json@v1.0.0"
      with:
        composer_file: "path/to/composer.json"
```

## debugging

You don't know how the key wanted looks like? Enable debugging and all composer env-variables will be printed during
a running workflow.

``` yaml
    - name: "Read Composer file"
      id: "composer"
      uses:  "flagbit/read-composer-json@v1.0.0"
      with:
        debug: "1"
```
