
name: Dynamic README injection
on:
  schedule: # Run workflow automatically
    # This will make it run every hour
    - cron: "0 * * * *"

  workflow_dispatch:
jobs:
  get-office-quotes:
    # job steps
        ...

  update-readme-with-blog:
    needs: get-office-quotes
    name: Update this repo's README with latest blog posts
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: gautamkrishnar/blog-post-workflow@master
        with:
          # Replace this URL with your rss feed URL/s
          feed_list: "https://braydoncoyer.hashnode.dev/rss.xml"

