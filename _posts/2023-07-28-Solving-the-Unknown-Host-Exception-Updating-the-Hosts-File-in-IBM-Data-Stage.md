---
layout: post
title:  Solving the Unknown Host Exception Updating the Hosts File in IBM Data Stage
date:   2023-07-28 12:11 +0330
lang: en
categories: english tech
---
In the banking industry, it is common to upload millions of records to a Hadoop cluster for future use. To perform this task, IBM Data Stage is used for ETL operations, which involves converting data to CSV files and storing them in HDFS. The File Connector component is utilized by data engineers to upload these files. However, when executing parallel jobs on a new IBM Data Stage server, a security network issue results in the Unknown Host Exception. This problem can be resolved by adding the IP and DNS of the NameNode and all DataNodes to the *hosts* file on the IBM Data Stage server.

It is essential to note that when expanding the Hadoop cluster, the *hosts* file must also be updated with the IP and DNS of the new machines. This is because the NameNode selects new machines for data distribution, leading to different unknown host names in each run. Therefore, adding the new machines to the *hosts* file on the IBM Data Stage server is necessary.


Sure, here's an example markdown for updating the *hosts* file when expanding a Hadoop cluster:

1. Open the *hosts* file on the IBM Data Stage server. This file is typically located in the `/etc` directory.

2. Add a new entry for the new machine in the *hosts* file, using its IP address and DNS name. For example:

   ```
   192.168.1.4 datanode3.example.com
   ```

3. Save the changes to the *hosts* file and exit the editor.

4. Restart the IBM Data Stage server to ensure that the changes take effect.

By following these steps, you can ensure that the IBM Data Stage server can communicate with all machines in the Hadoop cluster, including any new machines that you add in the future.

Sure, here's a possible rephrased version of the sentence:

The Unknown Host Exception appears in the following situations:

![File_Connector_2,0: An exception occurred: java.net.UnknownHostException]({{site.baseurl}}/docs/assets/images/ibm-data-stage-unknown-host-exception.jpg)

<mark>
<b>File Connector: An exception occurred: java.net.UnknownHostException</b> : <b>DNS Name of unknown host in out hadoop cluster</b> : <b>DNS Name of unknown host in out hadoop cluster</b>: unknown error</mark>
                at java.net.InetAddress.getAllByName0(InetAddress.java:1413)
                at java.net.InetAddress.getAllByName(InetAddress.java:1322)
                at java.net.InetAddress.getAllByName(InetAddress.java:1245)
                at org.apache.http.impl.conn.SystemDefaultDnsResolver.resolve(SystemDefaultDnsResolver.java:45)
                at org.apache.http.impl.conn.DefaultClientConnectionOperator.resolveHostname(DefaultClientConnectionOperator.java:262)
                at org.apache.http.impl.conn.DefaultClientConnectionOperator.openConnection(DefaultClientConnectionOperator.java:161)
                at org.apache.http.impl.conn.ManagedClientConnectionImpl.open(ManagedClientConnectionImpl.java:328)
                at org.apache.http.impl.client.DefaultRequestDirector.tryConnect(DefaultRequestDirector.java:612)
                at org.apache.http.impl.client.DefaultRequestDirector.execute(DefaultRequestDirector.java:447)
                at org.apache.http.impl.client.AbstractHttpClient.doExecute(AbstractHttpClient.java:884)
                at org.apache.http.impl.client.CloseableHttpClient.execute(CloseableHttpClient.java:82)
                at org.apache.http.impl.client.CloseableHttpClient.execute(CloseableHttpClient.java:107)
                at org.apache.http.impl.client.CloseableHttpClient.execute(CloseableHttpClient.java:55)
                at com.ibm.iis.cc.filesystem.impl.webhdfs.WebHDFS.appendFromBuffer(WebHDFS.java:320)
                at com.ibm.iis.cc.filesystem.impl.webhdfs.WebHDFS.writeFromStream(WebHDFS.java:212)
                at com.ibm.iis.cc.filesystem.AbstractFileSystem.writeFromStream(AbstractFileSystem.java:49)
                at com.ibm.iis.cc.filesystem.FileSystem$Uploader.call(FileSystem.java:4213)
                at com.ibm.iis.cc.filesystem.FileSystem$Uploader.call(FileSystem.java:4176)
                at java.util.concurrent.FutureTask.run(FutureTask.java:277)
                at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1160)
                at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:635)
                at java.lang.Thread.run(Thread.java:811)
<mark><b>An exception occurred: java.lang.RuntimeException: java.io.IOException: Pipe closed</b></mark>
                at com.ibm.iis.jis.utilities.delimited.DelimitedBuilder.close(DelimitedBuilder.java:282)
                at com.ibm.iis.jis.utilities.dochandler.impl.OutputBuilder.close(OutputBuilder.java:108)
                at com.ibm.iis.cc.filesystem.FileSystem.writeFile(FileSystem.java:948)
                at com.ibm.iis.cc.filesystem.FileSystem.process(FileSystem.java:818)
                at com.ibm.is.cc.javastage.connector.CC_JavaAdapter.run(CC_JavaAdapter.java:443)
<mark><b>Caused by: java.io.IOException: Pipe closed</b></mark>
                at java.io.PipedInputStream.checkStateForReceive(PipedInputStream.java:271)
                at java.io.PipedInputStream.receive(PipedInputStream.java:237)
                at java.io.PipedOutputStream.write(PipedOutputStream.java:160)
                at java.io.BufferedOutputStream.flushBuffer(BufferedOutputStream.java:93)
                at java.io.BufferedOutputStream.write(BufferedOutputStream.java:137)
                at java.io.BufferedOutputStream.flushBuffer(BufferedOutputStream.java:93)
                at java.io.BufferedOutputStream.flush(BufferedOutputStream.java:151)
                at com.ibm.iis.jis.utilities.delimited.DelimitedBuilder.close(DelimitedBuilder.java:278)
                ... 4 more
<mark><b>Caused by java.io.IOException: Pipe closed</b></mark>
                at java.io.PipedInputStream.checkStateForReceive(PipedInputStream.java:271)
                at java.io.PipedInputStream.receive(PipedInputStream.java:237)
                at java.io.PipedOutputStream.write(PipedOutputStream.java:160)
                at java.io.BufferedOutputStream.flushBuffer(BufferedOutputStream.java:93)
                at java.io.BufferedOutputStream.write(BufferedOutputStream.java:137)
                at java.io.BufferedOutputStream.flushBuffer(BufferedOutputStream.java:93)
                at java.io.BufferedOutputStream.flush(BufferedOutputStream.java:151)
                at com.ibm.iis.jis.utilities.delimited.DelimitedBuilder.close(DelimitedBuilder.java:278)
                at com.ibm.iis.jis.utilities.dochandler.impl.OutputBuilder.close(OutputBuilder.java:108)
                at com.ibm.iis.cc.filesystem.FileSystem.writeFile(FileSystem.java:948)
                at com.ibm.iis.cc.filesystem.FileSystem.process(FileSystem.java:818)
