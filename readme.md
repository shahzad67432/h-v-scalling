### clustring -> convering the single threaded to multiple threads.
    import cluster from "cluster";
    import os from "os";
    
    const totalCPUs = os.cpus().length;
    
    const port = 3000;
    
    if (cluster.isPrimary) {
      console.log(`Number of CPUs is ${totalCPUs}`);
      console.log(`Primary ${process.pid} is running`);
    
      // Fork workers.
      for (let i = 0; i < totalCPUs; i++) {
        cluster.fork();
      }
    
      cluster.on("exit", (worker, code, signal) => {
        console.log(`worker ${worker.process.pid} died`);
        console.log("Let's fork another worker!");
        cluster.fork();
      });
    } else {
        ### const app = express(); or do whatever you like to do;
    }

## this much code is enough 