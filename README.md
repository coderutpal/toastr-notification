# Toastr Notification Snippet for Livewire

This repository contains a reusable Toastr notification setup example with Livewire event dispatch and JavaScript listener.

## Features

- Uses Toastr CDN for notifications
- Listens for `showToastr` event in JavaScript
- Example Livewire PHP component that dispatches notifications

## Usage

1. Include Toastr CSS and JS CDN in your blade/layout:

```html
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/toastr.js/latest/toastr.min.css" />
<script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/toastr.js/latest/toastr.min.js"></script>


2. Add this script at the bottom of your layout (before closing </body>):

```html
<script>
    window.addEventListener('showToastr', function (event) {
        toastr.options = {
            closeButton: true,
            progressBar: true,
            positionClass: "toast-top-right",
        };

        if (event.detail.type === 'success') {
            toastr.success(event.detail.message);
        } else if (event.detail.type === 'error') {
            toastr.error(event.detail.message);
        } else if (event.detail.type === 'info') {
            toastr.info(event.detail.message);
        } else if (event.detail.type === 'warning') {
            toastr.warning(event.detail.message);
        }
    });
</script>


3. Dispatch Toastr event from your Livewire component:

```html
$this->dispatch('showToastr', [
    'type' => 'success', // success, error, info, warning
    'message' => 'Your custom notification message'
]);


Optional: Use local Toastr assets
Download toastr.min.css and toastr.min.js files and place them in your project’s public folder.

Then include them like this:


```html
<link rel="stylesheet" href="{{ asset('css/toastr.min.css') }}">
<script src="{{ asset('js/toastr.min.js') }}"></script>
