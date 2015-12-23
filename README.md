# pip2s3

Small utility allowing easy creation of pip servers in s3, by functionality between pip2pi and aws s3 sync.

## Installation

### Homebrew
Mac OS X users can install pip2s3 with the Homebrew package manager. This will give you access to the pip2s3 command.

     $ brew tap drewsonne/devops
     $ brew install pip2s3
     
## Usage

### CLI
   `AWS_*=value pip2s3 s3_bucket [project_folder]`
   
 - `s3_bucket` URI prefixed by `s3://` describing the bucket and path to push the pip mirror to  
 - `project_folder` is the path to a directory containing a 'requirements.txt' file, with a list of pip packages to download and mirror to s3


### Arguments
 
    - s3_bucket           Path to an s3 bucket and key. eg, s3://mybucket/key.
    - project_folder      Path to a folder with requirements.txt in it. Default is current working directory.

### Environment Variables
 
 Environment variable     | Description          
--------------------------|----------------------
 `$AWS_ACCESS_KEY_ID`      | AWS access key 
 `$AWS_SECRET_ACCESS_KEY`  | AWS secret key. Access and secret key variables override credentials stored in credential and config files. 
 `$AWS_SESSION_TOKEN`      | session token. A session token is only required if you are using temporary security credentials.
 `$AWS_DEFAULT_REGION`     | AWS region. This variable overrides the default region of the in-use profile, if set.
 `$AWS_DEFAULT_PROFILE`    | name of the CLI profile to use. This can be the name of a profile stored in a credential or config file, or default to use the default profile. 
 `$AWS_CONFIG_FILE`        | path to a CLI config file.

## Configuration
After running this script, you can access your packages by either configuring the file
/etc/pip.conf, or add --extra-index-url=http://your-s3-bucket/packages/simple/ to your pip
command. The configuration for /etc/pip.conf is is composed of:

    [global]
    extra_index_url = http://your-s3-bucket/packages/simple/

You can now use pip install my_package in the normal manner and refer to packages in this s3 repository.
