# Unpoly for AdonisJS 6

Easily add support for the server protocol expected by [Unpoly](http://unpoly.com).

## Installation


```bash
node ace add @jrmc/adonis-unpoly
```

Or 

```bash
npm install @jrmc/adonis-unpoly
node ace configure @jrmc/adonis-unpoly
```

## Usage in controllers

Sample close drawer or redirect

```javascript
  async store({ response, i18n, up }: HttpContext) {
    // ...

    session.flash('notification', {
      type: 'success',
      message: i18n.formatMessage('form.success.user.create'),
    })

    if (up.isDrawer()) {
      up.setDismissLayer()
    } else {
      response.redirect().toRoute('admin.users.index')
    }
  }
```

## Usage in edge view

Sample back button

```edge
@if(up.isDrawer())
  <button up-dismiss>
    @svg('tabler:arrow-left')
  <button>
@else
  <a href="{{ $props.href }}">
    @svg('tabler:arrow-left')
  </a>
@end
```
