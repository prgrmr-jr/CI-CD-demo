# Steps in Self-Hosted GitHub Actions

To set up and use self-hosted runners in GitHub Actions, follow these steps:

## 1. Prepare the Self-Hosted Runner

1. **Create a Runner**:
    - Go to your repository on GitHub.
    - Navigate to **Settings** > **Actions** > **Runners**.
    - Click **Add runner** and follow the instructions to download and configure the runner.

2. **Install the Runner**:
    - Download the runner application.
    - Extract the downloaded file.
    - Configure the runner by running the provided configuration command.

3. **Run the Runner**:
    - Start the runner using the command provided in the setup instructions.

4. **Verify the Runner**:
    - Go to the **Actions** tab in your repository.
    - Check if the self-hosted runner is listed under **Self-hosted runners**.

5. **Run the Runner always**:
    - To run the runner always, you can use the following command:
    ```sh
    sudo ./svc.sh install
    sudo ./svc.sh start
    ```
    - This will make the runner as a service and start it automatically.

## 2. Configure GitHub Actions Workflow

1. **Create a Workflow File**:
    - In your repository, create a new file in the `.github/workflows` directory, e.g., `self-hosted-runner.yml`.

2. **Define the Workflow**:
    - Use the following example to define a workflow that uses the self-hosted runner:

    ```yaml
    name: Node.js CI

    on:
        push:
            branches: [ "main" ]
        pull_request:
            branches: [ "main" ]

        jobs:
            build:

                runs-on: self-hosted

            strategy:
                matrix:
                    node-version: [18.x, 20.x, 22.x]

        steps:
    - uses: actions/checkout@v4
    - name: Use Node.js ${{ matrix.node-version }}
      uses: actions/setup-node@v4
      with:
        node-version: ${{ matrix.node-version }}
        cache: 'npm'
    - run: npm ci
    - run: npm run build --if-present
    - run: npm test

    ```

## 3. Run the Workflow

1. **Trigger the Workflow**:
    - Push changes to the repository or create a pull request to trigger the workflow.

2. **Monitor the Workflow**:
    - Go to the **Actions** tab in your repository to monitor the progress and results of the workflow.

By following these steps, you can set up and use self-hosted runners in your GitHub Actions workflows.
