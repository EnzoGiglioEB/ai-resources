---
name: webapp-testing
description: "Automated web application testing. Use this skill when users need to test web applications, verify functionality, check responsiveness, validate forms, or perform automated browser testing"
license: Apache 2.0
---

# Webapp Testing

## Overview

Automated testing for web applications using browser automation and testing frameworks.

## Capabilities

### Browser Automation
- **Element discovery**: Locate and interact with page elements
- **User interactions**: Click, type, scroll, hover
- **Navigation**: Page loads, redirects, multi-page flows
- **Screenshots**: Capture visual state

### Testing Scenarios
- **Functional testing**: Verify features work correctly
- **Responsive testing**: Check different screen sizes
- **Form validation**: Test input validation and submission
- **Console logging**: Monitor browser console for errors
- **Network requests**: Track API calls and responses

## Key Tools

### Selenium/WebDriver
Browser automation for testing

```python
from selenium import webdriver
from selenium.webdriver.common.by import By

driver = webdriver.Chrome()
driver.get('https://example.com')
element = driver.find_element(By.ID, 'submit-btn')
element.click()
```

### Static HTML Testing
For testing static sites or HTML artifacts

**Reference**: See `examples/static_html_automation.py`

### Server-based Testing
For testing applications with backends

**Reference**: See `scripts/with_server.py`

## Workflows

### Basic Test Workflow
1. Set up test environment
2. Navigate to target page
3. Perform actions (click, type, etc.)
4. Verify expected results
5. Clean up and report

### Element Discovery
```python
# Multiple strategies
element = driver.find_element(By.ID, 'element-id')
element = driver.find_element(By.CLASS_NAME, 'btn-primary')
element = driver.find_element(By.CSS_SELECTOR, 'button.submit')
element = driver.find_element(By.XPATH, '//button[@type="submit"]')
```

**Reference**: See `examples/element_discovery.py`

### Console Logging
Monitor browser console for errors and warnings

```python
# Get console logs
logs = driver.get_log('browser')
for log in logs:
    print(f"{log['level']}: {log['message']}")
```

**Reference**: See `examples/console_logging.py`

## Common Test Patterns

### Form Testing
```python
# Fill and submit form
name_input = driver.find_element(By.ID, 'name')
name_input.send_keys('Test User')

email_input = driver.find_element(By.ID, 'email')
email_input.send_keys('test@example.com')

submit_btn = driver.find_element(By.CSS_SELECTOR, 'button[type="submit"]')
submit_btn.click()

# Verify success
success_msg = driver.find_element(By.CLASS_NAME, 'success-message')
assert 'Thank you' in success_msg.text
```

### Responsive Testing
```python
# Test different viewports
viewports = [
    (375, 667),   # Mobile
    (768, 1024),  # Tablet
    (1920, 1080)  # Desktop
]

for width, height in viewports:
    driver.set_window_size(width, height)
    # Run tests for this viewport
```

### Wait for Elements
```python
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC

# Wait up to 10 seconds for element
element = WebDriverWait(driver, 10).until(
    EC.presence_of_element_located((By.ID, 'dynamic-element'))
)
```

## Best Practices

1. **Use explicit waits** instead of sleep()
2. **Test in multiple browsers** (Chrome, Firefox, Safari)
3. **Clean up resources** (close drivers, kill servers)
4. **Capture screenshots** on failures
5. **Test responsiveness** at key breakpoints
6. **Monitor console** for JavaScript errors

## Bundled Resources

### Examples
- `examples/static_html_automation.py` - Testing static HTML
- `examples/element_discovery.py` - Finding elements
- `examples/console_logging.py` - Console monitoring

### Scripts
- `scripts/with_server.py` - Testing with local server

---

**Note**: Requires Selenium WebDriver and appropriate browser drivers (chromedriver, geckodriver, etc.). Examples demonstrate common testing patterns and best practices.
