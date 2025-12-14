# DemoEvershop Search Feature Test Cases

This document contains detailed manual test cases, API and UI test execution results for the Search functionality of the DemoEvershop e-commerce site. The test cases cover product search, partial search, typo handling, autocomplete suggestions, filters, sorting, out-of-stock items, multi-variant products, and happy path journey for adding products to the cart.

---

## Precondition
- DemoEvershop website is accessible
- Search bar is visible and enabled
- Products exist with the following attributes: name, brand, category, color, size, SKU
- Search service is active
- Test data is available
- Cart is empty before starting happy path journey

---

## Test Cases Summary

| TC ID | Scenario | Expected Result |
|-------|---------|----------------|
| TC-01 | Search by Product Name | Matching products displayed |
| TC-02 | Partial Keyword Search | Relevant products displayed |
| TC-03 | Typo Handling | Relevant products displayed (fuzzy match) |
| TC-04 | Autocomplete Suggestions | Suggestions appear dynamically |
| TC-05 | Out-of-Stock Products | Products shown according to business rule |
| TC-06 | Filter Search Results | Filters applied correctly |
| TC-07 | Sort Search Results | Products sorted correctly |
| TC-08 | Voice Search | Works if supported |
| TC-09 | Non-Product Pages Search | Relevant pages displayed |
| TC-10 | Multi-Variant Products | Variants displayed grouped or separate according to rule |
| TC-11 | Happy Path Cart Journey | Selected products with multiple sizes/colors added correctly to cart |

---

## Test Execution Results
- Total Test Cases: 11
- Passed: 8
- Failed: 3
- Not Applicable: 1

### Remarks
- Typo handling did not work for some misspelled words
- Non-product pages are not included in search results
- Some variant handling issues in cart
- All other scenarios passed successfully

---

## API and UI Happy Path Journey
1. **Search API**: `/api/products?search=Nike+react` → validated product list, attributes, stock
2. **Add to Cart API**: `/api/cart/add` → selected variants added successfully
3. **Cart Verification API**: `/api/cart` → all items, quantities, sizes, colors verified
4. **UI Testing**: Search 'Nike react', select first items, add multiple sizes/colors to cart, verify cart content matches API results

### Defect Summary

| Defect ID | Description | Severity | Steps to Reproduce | Status |
|-----------|------------|----------|------------------|--------|
| BUG-01 | Cart shows wrong total for multiple variants | Medium | Add 2x black, small Nike React shoes, check cart | Open |
| BUG-02 | Search API returns incomplete results | High | Search 'Nike react' | Open |
| BUG-03 | UI cart does not reflect API cart additions | High | Add via API, check UI cart | Open |

---

## Additional Notes
- Screenshots and evidence are stored in the `test-evidence/` folder
- Test cases executed manually and via API on [DemoEvershop](https://demo.evershop.io/)
- Logs of all API responses and UI actions maintained
- Some behaviors may vary based on final business rules
