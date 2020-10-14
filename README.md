# ansible_tries


```
osboxes@osboxes:~/ansible_tests$ time ansible-playbook async.yaml
[WARNING]: provided hosts list is empty, only localhost is available. Note that the implicit localhost does not match 'all'

PLAY [update web servers] ***************************************************************************************************************************************************

TASK [Gathering Facts] ******************************************************************************************************************************************************
ok: [localhost]

TASK [ensure apache is at the latest version] *******************************************************************************************************************************
ok: [localhost] => {
    "msg": "Hello"
}

TASK [Read users from CSV file and return a dictionary] *********************************************************************************************************************
ok: [localhost -> localhost]

TASK [debug] ****************************************************************************************************************************************************************
ok: [localhost] => {
    "msg": "User dag has UID 500 and GID 500"
}

TASK [Count our fruit] ******************************************************************************************************************************************************
changed: [localhost] => (item=apple)
changed: [localhost] => (item=banana)
changed: [localhost] => (item=pear)

TASK [loop through list from a variable] ************************************************************************************************************************************
ok: [localhost] => (item=dag) => {
    "msg": "An item: dag"
}
ok: [localhost] => (item=jeroen) => {
    "msg": "An item: jeroen"
}
ok: [localhost] => (item=kiran) => {
    "msg": "An item: kiran"
}

TASK [do something] *********************************************************************************************************************************************************
changed: [localhost] => (item=dag)
changed: [localhost] => (item=jeroen)
changed: [localhost] => (item=kiran)

TASK [check if something is done] *******************************************************************************************************************************************
changed: [localhost] => (item=dag)
changed: [localhost] => (item=jeroen)
FAILED - RETRYING: check if something is done (3 retries left).
FAILED - RETRYING: check if something is done (2 retries left).
changed: [localhost] => (item=kiran)

TASK [wait till all somethings tasks are done] ******************************************************************************************************************************
changed: [localhost] => (item={'cmd': 'test -d /home/osboxes/ansible_tests/test/dag', 'stdout': '', 'stderr': '', 'rc': 0, 'start': '2020-10-12 02:17:11.899557', 'end': '2020-10-12 02:17:11.901259', 'delta': '0:00:00.001702', 'changed': True, 'invocation': {'module_args': {'_raw_params': 'test -d /home/osboxes/ansible_tests/test/dag', '_uses_shell': True, 'warn': True, 'stdin_add_newline': True, 'strip_empty_ends': True, 'argv': None, 'chdir': None, 'executable': None, 'creates': None, 'removes': None, 'stdin': None}}, 'finished': 1, 'ansible_job_id': '136946941822.338470', 'stdout_lines': [], 'stderr_lines': [], 'failed': False, 'attempts': 1, 'item': 'dag', 'ansible_loop_var': 'item'})
changed: [localhost] => (item={'cmd': 'test -d /home/osboxes/ansible_tests/test/jeroen', 'stdout': '', 'stderr': '', 'rc': 0, 'start': '2020-10-12 02:18:12.251998', 'end': '2020-10-12 02:18:12.253762', 'delta': '0:00:00.001764', 'changed': True, 'invocation': {'module_args': {'_raw_params': 'test -d /home/osboxes/ansible_tests/test/jeroen', '_uses_shell': True, 'warn': True, 'stdin_add_newline': True, 'strip_empty_ends': True, 'argv': None, 'chdir': None, 'executable': None, 'creates': None, 'removes': None, 'stdin': None}}, 'finished': 1, 'ansible_job_id': '966849477440.338525', 'stdout_lines': [], 'stderr_lines': [], 'failed': False, 'attempts': 1, 'item': 'jeroen', 'ansible_loop_var': 'item'})
changed: [localhost] => (item={'cmd': 'test -d /home/osboxes/ansible_tests/test/kiran', 'stdout': '', 'stderr': '', 'rc': 0, 'start': '2020-10-12 02:21:23.002217', 'end': '2020-10-12 02:21:23.004216', 'delta': '0:00:00.001999', 'changed': True, 'invocation': {'module_args': {'_raw_params': 'test -d /home/osboxes/ansible_tests/test/kiran', '_uses_shell': True, 'warn': True, 'stdin_add_newline': True, 'strip_empty_ends': True, 'argv': None, 'chdir': None, 'executable': None, 'creates': None, 'removes': None, 'stdin': None}}, 'finished': 1, 'ansible_job_id': '214528821291.338715', 'stdout_lines': [], 'stderr_lines': [], 'failed': False, 'attempts': 3, 'item': 'kiran', 'ansible_loop_var': 'item'})

PLAY RECAP ******************************************************************************************************************************************************************
localhost                  : ok=9    changed=4    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0


real    5m14.140s
user    0m10.676s
sys     0m2.235s

```
