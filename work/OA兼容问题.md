1. 问题现象  
    使用手机浏览器或者非ie内核的PC浏览器打开OA网页，进行审批提交时，时常出现无法正常提交的现象。
2. 问题分析  
通过对OA系统代码的跟踪排查，这类情况通常是由于OA网页的HTML和JavaScript代码兼容性差引起的。追溯OA系统的历史，根本原因是设计之初，只针对IE浏览器开发，没有考虑浏览器兼容性问题，导致OA网页的HTML和JavaScript代码中存在大量诸如以下代码的bug：

    ```HTML
    <INPUT type="hidden" value="0" name="flag_qitaxueli1">
    ```
    ```JavaScript
    document.getElementById('flag_qitaxueli1').value = flag_qitaxueli1;
    ```
    以上代码在IE内核的浏览器中可以正常执行，但在Firefox、Chrome以及手机浏览器中就会返回NULL，导致流程无法正常提交。  
3. 存在难点  
   - OA系统的代码必须在domino客户端进行编写/修改，多人协作相对困难；
   - OA系统的代码框架原始，代码不具备可重用性，故必须对OA所有流程的页面逐一修复，效率低，工作量大；
   - 代码重构必须建立在业务逻辑清晰的前提下，目前OA维护几经转手，开发商/维护厂商也多次变动，部分业务逻辑已经无从追踪，若要重构，需相关业务部门配合重新整理业务逻辑；
