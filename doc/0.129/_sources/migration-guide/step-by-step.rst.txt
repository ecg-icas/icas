This section provides a detailed view of the changes for each affected API endpoint, mapping fields from the old and deprecated versions to the new `v5`.
Follow this guide to understand the modifications and learn how to update your implementation for a smooth migration.

Each API endpoint is presented in a expandable/collapsible section, with the deprecated and new versions side by side for easy comparison.


.. raw:: html

   <details open>
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
   <summary><code>GET /ad/ (list)</code></summary>

   <br>

   <div style="display: flex; gap: 20px;">

   <div style="flex: 1; padding-right: 10px;">
   <p><strong>Request payload: deprecated version</strong></p>

.. include:: migration-guide/get-ads-payload-old.rst

.. raw:: html

   </div>
   <div style="flex: 1; padding-left: 10px;">
   <p><strong>Request payload: new version</strong></p>

.. include:: migration-guide/get-ads-payload-new.rst

.. raw:: html

   </div>
   </div>

   <div>
   <p><strong>Mapping details</strong></p>

.. include:: migration-guide/get-ads-mapping.rst

.. raw:: html

   </div>
   </details>


.. raw:: html

   <details>
   <summary><code>PUT /ad/{id}/status/{status}</code></summary>

   <br>

   <div>

.. include:: migration-guide/put-ad-status-mapping.rst

.. raw:: html

   </div>
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

**Summary of API version changes**

.. list-table::
   :header-rows: 1
   :widths: 20 30 20
   :align: center

   * - **API Endpoint**
     - **Deprecated Versions**
     - **New Version**
   * - ``GET /ad/{id}``
     - ``v2``, ``v3``
     - ``v5``
   * - ``GET /ad/byVendor/{vendorId}``
     - ``v2``, ``v3``
     - ``v5``
   * - ``POST /ad``
     - ``v2``, ``v3``
     - ``v5``
   * - ``PUT /ad/{id}``
     - ``v2``, ``v3``
     - ``v5``
   * - ``GET /ad/ (list)``
     - ``v4``
     - ``v5``
   * - ``PUT /ad/{id}/status/{status}``
     - unversioned
     - ``v5``
   * - ``GET /categories``
     - ``v1``
     - ``v5``
   * - ``GET /category/{id}``
     - ``v1``
     - ``v5``
