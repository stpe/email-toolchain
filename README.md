Stefan's Email Toolchain
========================
Now and then there is a need to construct HTML emails for various triggers, drip feeds, campaigns, etc. This is a handy toolchain (evolving every time I need to use it) that currently take care of...

 * Multiple email templates
 * Use of partials/include (with parameters)
 * Replace placeholders with values from JSON (template constants)
 * Inline CSS automatically
 * Upload images automatically to AWS S3

 Everything automated using [Grunt](http://gruntjs.com/).

## Installation

`gem install premailer`
`npm install`

## Configuration

### AWS S3 credentials

`grunt-aws.json`
```
{
    "key": "KGSURJNKRU847NBSJH48",
    "secret": "adkGU488jsku49belirx49vnSD4gsSgbnDSu48SD",
    "bucket": "email.company.com",
    "bucketdir": "emailassets/gfx",
    "region": "eu-west-1"
}
```

### Template Constants

Use `@@mykey` in template to have it replaced by value in `constants.json`:
```
{
    "mykey": "http://support.company.com/",
    "hello": "Greetings!"
}
```

## Usage

`grunt`
`grunt upload`

Put template in `templates/`. Partials used by templates in `templates/partials/` and images in `templates/gfx/`.
Every template will be processed and result in a separate output file put in `dist/`.