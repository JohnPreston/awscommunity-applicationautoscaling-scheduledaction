# AwsCommunity::ApplicationAutoscaling::ScheduledAction

This resource allows to create a Scheduled Action via Application Autoscaling for a given resource.
Currently on AWS the only actions are TargetTracking and Step Scaling. So this aims to bridge that gap.


## Testing

Create 2 virtual environments after cloning the repository: one for SAM CLI, one for CFN and our resource.

```shell
python -m venv sam-cli
source sam-cli/bin/activate
pip install pip -U; pip install aws-sam-cli
sam local start-lambda`
```

In a different terminal / session, install the resource and depencencies
```shell
poetry env use 3.9 # You can use another python version, but I recommend to stick to the ones supported by AWS Lambda
poetry install
# Activate it.
source `poetry env info -p`/bin/activate
```

Run `make package` to create the `build` layer that is used by SAM CLI.
Change the values in `inputs/*.json` to match the resource you have in your account you can perform the tests with,
then you can test using `cfn test`


## Build the ZIP for the resource and definition

```shell
make zip
```

## Create the execution role.

Using the `resource-role.yaml`, create the execution role that will allow you to run the resource.


## Publishing

You can publish and register the resource using the `publish.template` CFN Template.
