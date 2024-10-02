
# General Information About Grid5000 (Grid5k)

Grid5000 (Grid5k) is a large-scale and versatile testbed for research in distributed systems, cloud computing, and big data. It consists of several clusters located in various sites across France. Grid5k offers an environment where users can deploy their own software stacks and conduct experiments on distributed systems.

## Resource Reservation Procedure in Grid5k (Passive Mode)

When using Grid5k, one key feature is the resource reservation system. The "passive mode" allows users to reserve resources without actively connecting to them until they are needed. Here’s how the process works:

### Steps for Resource Reservation in Passive Mode:

- **1. Authentication**: 
  You must authenticate yourself using your Grid5k account credentials.

  \`\`\`shell
  ssh your-username@access.grid5000.fr
  \`\`\`

- **2. Using `oarsub` to Reserve Resources**: 
  The `oarsub` command is used to submit a resource reservation. In passive mode, you specify the number of resources, duration, and the type of nodes required for the experiment.

  Example of reserving 5 nodes for 2 hours in passive mode:

  \`\`\`shell
  oarsub -I -l nodes=5,walltime=2:00:00
  \`\`\`

- **3. Wait for Resources to Become Available**: 
  After submitting the reservation, you wait for the resources to become available. In passive mode, the resources are reserved, but you are not yet connected to them.

- **4. Check Reservation Status**: 
  You can check the status of your reservation to know when the resources are ready using the `oarstat` command.

  \`\`\`shell
  oarstat -u
  \`\`\`

- **5. Connecting to Reserved Resources**: 
  Once the resources are available, you can connect to the nodes by using the `oarsub -C` command. This command will attach you to the reserved resources in passive mode.

  \`\`\`shell
  oarsub -C <job_id>
  \`\`\`

- **6. Releasing Resources**: 
  After your experiment, you can release the resources by simply exiting the session, or by using the `oardel` command to cancel the reservation explicitly.

  \`\`\`shell
  oardel <job_id>
  \`\`\`

### Key Points About Passive Mode:

- **Passive Mode**: In this mode, resources are reserved but you only connect to them when needed, using `oarsub -C`.
- **Job ID**: Each reservation is assigned a job ID, which you use to manage and monitor the reserved resources.
- **`oarsub` Command**: This command is essential for reserving resources and starting a job.
- **`oarstat` and `oardel` Commands**: These commands help you monitor and cancel reservations, respectively.

By following these steps, you can efficiently reserve and manage computing resources on Grid5k using the passive mode.
