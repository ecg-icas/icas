This section provides a detailed overview of the changes for each affected API endpoint, mapping fields from the old and deprecated versions to the new `v5`.
Follow this guide to understand the modifications and learn how to update your implementation for a smooth migration.

.. raw:: html

   <details>
   <summary><code>GET /ad/{id}</code></summary>

   <br>

   <div style="display: flex; gap: 20px;">

   <div style="flex: 1; padding-right: 10px;">
   <p><strong>Response payload: deprecated version</strong></p>

.. include:: migration-guide/get-ad-payload-old.rst

.. raw:: html

   </div>
   <div style="flex: 1; padding-left: 10px;">
   <p><strong>Response payload: new version</strong></p>

.. include:: migration-guide/get-ad-payload-new.rst

.. raw:: html

   </div>
   </div>

   <div>
   <p><strong>Mapping details</strong></p>

.. include:: migration-guide/get-ad-mapping.rst

.. raw:: html

   </div>
   </details>

.. raw:: html

   <details>
   <summary><code>GET /ad/byVendor/{vendorId}</code></summary>

   <br>

   <div style="display: flex; gap: 20px;">

   <div style="flex: 1; padding-right: 10px;">
   <p><strong>Response payload: deprecated version</strong></p>

.. include:: migration-guide/get-ad-payload-old.rst

.. raw:: html

   </div>
   <div style="flex: 1; padding-left: 10px;">
   <p><strong>New version</strong></p>

.. include:: migration-guide/get-ad-payload-new.rst

.. raw:: html

   </div>
   </div>

   <div>
   <p><strong>Mapping details</strong></p>

.. include:: migration-guide/get-ad-mapping.rst

.. raw:: html

   </div>
   </details>



.. raw:: html

   <details>
   <summary><code>POST /ad</code></summary>

   <br>

   <div style="display: flex; gap: 20px;">

   <div style="flex: 1; padding-right: 10px;">
   <p><strong>Request payload: deprecated version</strong></p>

.. include:: migration-guide/post-ad-payload-old.rst

.. raw:: html

   </div>
   <div style="flex: 1; padding-left: 10px;">
   <p><strong>Request payload: new version</strong></p>

.. include:: migration-guide/post-ad-payload-new.rst

.. raw:: html

   </div>
   </div>

   <div>
   <p><strong>Mapping details</strong></p>

.. include:: migration-guide/post-ad-mapping.rst

.. raw:: html

   </div>
   </details>



.. raw:: html

   <details>
   <summary><code>PUT /ad/{id}</code></summary>

   <br>

   <div style="display: flex; gap: 20px;">

   <div style="flex: 1; padding-right: 10px;">
   <p><strong>Request payload: deprecated version</strong></p>

.. include:: migration-guide/post-ad-payload-old.rst

.. raw:: html

   </div>
   <div style="flex: 1; padding-left: 10px;">
   <p><strong>Request payload: new version</strong></p>

.. include:: migration-guide/post-ad-payload-new.rst

.. raw:: html

   </div>
   </div>

   <div>
   <p><strong>Mapping details</strong></p>

.. include:: migration-guide/post-ad-mapping.rst

.. raw:: html

   </div>
   </details>


.. raw:: html

   <details>
   <summary><code>PUT /ad/{id}/status/{status}</code></summary>

   <br>
   Only change the media type to a versioned one <span style="font-family: monospace; color: red;">application/sellside.ad-v5+json</span>, it should be completely backwards compatible. See the :ref:`faq-migration` section for details.

   </details>



.. raw:: html

   <details>
   <summary><code>GET /categories</code></summary>

   <br>

   <div style="display: flex; gap: 20px;">

   <div style="flex: 1; padding-right: 10px;">
   <p><strong>Response payload: deprecated version</strong></p>

.. include:: migration-guide/get-categories-payload-old.rst

.. raw:: html

   </div>
   <div style="flex: 1; padding-left: 10px;">
   <p><strong>Response payload: new version</strong></p>

.. include:: migration-guide/get-categories-payload-new.rst

.. raw:: html

   </div>
   </div>

   <div>
   <p><strong>Mapping details</strong></p>

.. include:: migration-guide/get-categories-mapping.rst

.. raw:: html

   </div>
   </details>



.. raw:: html

   <details>
   <summary><code>GET /category/{id}</code></summary>

   <br>

   <div style="display: flex; gap: 20px;">

   <div style="flex: 1; padding-right: 10px;">
   <p><strong>Response payload: deprecated version</strong></p>

.. include:: migration-guide/get-categories-payload-old.rst

.. raw:: html

   </div>
   <div style="flex: 1; padding-left: 10px;">
   <p><strong>Response payload: new version</strong></p>

.. include:: migration-guide/get-categories-payload-new.rst

.. raw:: html

   </div>
   </div>

   <div>
   <p><strong>Mapping details</strong></p>

.. include:: migration-guide/get-category-mapping.rst

.. raw:: html

   </div>
   </details>




    <br><br>

