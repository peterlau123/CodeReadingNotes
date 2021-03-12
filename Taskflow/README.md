# Taskflow

## Repository Overview

The five key directories under the TFRT root directory are

*   `core/`: Contains core TFRT infrastructure code
*   `cuda/`: Contains device specific infrastructure and op/kernel
    implementations
*   `dsl/`: Contains public header files for core TFRT infrastructure
*   `tensorframe/`: Contains
*   `utility/`: Contains

<table>

  <tr>
   <td><strong>Top level directory</strong>
   </td>
   <td><strong>Sub-directory</strong>
   </td>
   <td>Main file name</td>
   <td><strong>File description</strong>
   </td>
  </tr>

  <tr>
   <td ><strong><code>core/</code></strong>
   </td>
   <td><code>algorithm</code></td>

   <td><code>executor.hpp</code></td>
   <td>provide taskflow excutor interfaces</td>

  </tr>

  <tr>
   <td ><strong><code>cuda/</code></strong>
   </td>
   <td>
   <code>cublas</code>
   </td>
   <td>Taskflow files GPU process
   </td>
  </tr>

  <tr>
  <td> </td><td><code>cuda_algorithm</code></td>
  <td></td>
  </tr>
   
   <tr>
   <td colspan=2><code>dsl</code></td>
   <td></td>
   </tr>

   <tr>
   <td colspan=2><code>tensorframe</code></td>
   <td></td>
   </tr>

  <tr>
   <td colspan=2><code>utility</code></td>
   <td></td>
   </tr> 
</table>