# Ansible role for GIT push to deploy

Configure GIT hooks by installing this role.

### Installation:
#### From ansible.galaxy :

__`ansible-galaxy install PrabhuVignesh.push_to_deploy`__

## Useage:
Just keep the workstation machine's public key in a file and mention the path of the file where public keys are stored.
(I mean Workstation machine as developer's machine)

 ```yml
 ---
  roles:
    - role: PrabhuVignesh.push_to_deploy
      path_for_authorized_keys: /path/to/public_key/file
      git_repository_path: /home/path/to/your/repo.git
      post_receive_script: "script to deploy the code"
      pre_receive_script: "Prepare storing code" 
   ```   

After the ansible playbook run, Workstation machine should have this remote in git repository

  __`git remote add production git@gitserver:repo.git`__
  
  when ever developer push the code to gitserver, script for _post-receive_ and _pre-receive_ will run. for example "_puppet deploy script_", "_cap deploy..._" etc.. Test 3
