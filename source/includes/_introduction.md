# Introduction

Welcome to the Kittn API! You can use our API to access Kittn API endpoints, which can get information on various cats, kittens, and breeds in our database.

We have language bindings in Shell, Ruby, and Python! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This example API documentation page was created with [Slate](https://github.com/tripit/slate). Feel free to edit it and use it as a base for your own API's documentation.


## Common Return Parameters

| Parameter | Type | Description |
| --------: | :--------: | :---------- |
| error_name | String | if the value of success is false, web backend needs to assign the name of error, unless this parameter should be empty.|
| validation | Object | if the err_name is illegal form input, web backend should assign the name of the wrong type for each error input |