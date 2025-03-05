# aws-login

## Usage

### Using default login server
```
jobs:
  build:
    steps:
    - name: Config AWS creds
      uses: fc-actions/aws-login@v0.0.1
      with:
        fireclover-client-id: ${{ vars.FIRECLOVER_CLIENT_ID }} 
        fireclover-client-secret: ${{ secrets.FIRECLOVER_CLIENT_SECRET }}
```

### Custom login server and identity token file
```
jobs:
  build:
    steps:
    - name: Config AWS creds
      uses: fc-actions/aws-login@v0.0.1
      with:
        fireclover-client-id: ${{ vars.FIRECLOVER_CLIENT_ID }} 
        fireclover-client-secret: ${{ secrets.FIRECLOVER_CLIENT_SECRET }}
        login-server-token-endpoint: 'https://dev.login.ms.fireclover.cloud/oauth2/token'
        aws-web-identity-token-file: 'some-folder/some-other-file'

    - name: Optionally Check the AWS creds
      if: false
      run: |
        cat $AWS_WEB_IDENTITY_TOKEN_FILE
        pip3 install awscli -q --break-system-packages
        aws sts get-caller-identity
```
