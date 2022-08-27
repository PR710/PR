name: PR
on:
  schedule:
  - cron:  '0 0 * * *'
  workflow_dispatch:

jobs:
  send_message:
    runs-on: ubuntu-latest
    name: send morning to your girlfriend

    steps:
    - name: checkout
      uses: actions/checkout@v3
      with:
        ref: master

    - name: sender
      uses: actions/setup-python@v2
      with:
        python-version: '3.x'
        architecture: 'x64'
    - run: pip install -r ./requirements.txt && python ./main.py

    env:
      APP_ID: ${{ secrets.APP_ID }}
      APP_SECRET: ${{ secrets.APP_SECRET }}
      TEMPLATE_ID: ${{ secrets.TEMPLATE_ID }}
      USER_ID: ${{ secrets.USER_ID }}
      START_DATE: ${{ secrets.START_DATE }}
      BIRTHDAY: ${{ secrets.BIRTHDAY }}
      CITY: ${{ secrets.CITY }}
      DATE:${{secrets.DATE}}
