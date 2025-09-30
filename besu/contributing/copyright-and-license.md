# Copyright and License

As per section 12.a of the [Hyperledger Charter](https://www.hyperledger.org/about/charter) all new code submitted to the Hyperledger Foundation needs to be under the Apache License, Version 2.0.

As per section 12.c of the [Hyperledger Charter](https://www.hyperledger.org/about/charter) all new documentation submitted to the Hyperledger Foundation needs to be under the Creative Commons Attribution 4.0 International License.  

You may maintain copyright to your works under these two clauses.

When you commit code please ensure you:

- put your copyright if required
- you MUST put the SPDX license header using Apache 2.0 like below. Otherwise, the build will fail the license header check.

`/* SPDX-License-Identifier: Apache-2.0 */`

  
This is now enforced by spotlessCheck and spotlessApply will automatically add it.

Example:

```
/*
 * Copyright contributors to Hyperledger Besu.
 *
 * Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with
 * the License. You may obtain a copy of the License at
 *
 * http://www.apache.org/licenses/LICENSE-2.0
 *
 * Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on
 * an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the
 * specific language governing permissions and limitations under the License.
 *
 * SPDX-License-Identifier: Apache-2.0
 */
```