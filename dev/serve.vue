<script>
import Vue from 'vue';
import {Button, Badge, Avatar, Card } from '@/entry';

export default Vue.extend({
  name: 'ServeDev',
  components: {
    Button,
    Badge,
    Avatar,
    Card
  }
});
</script>

<template>
  <div id="app">
    <h2>Button Types</h2>
    <div>
      <Button>Button</Button>
      <Button :wire="true">Button</Button>
      <Button :danger="true">Button</Button>
      <Button :wire="true" :danger="true">Button</Button>
      <Button :warning="true">Button</Button>
      <Button :wire="true" :warning="true">Button</Button>
      <Button :success="true">Button</Button>
      <Button :wire="true" :success="true">Button</Button>
      <Button :info="true">Button</Button>
      <Button :wire="true" :info="true">Button</Button>
    </div>
    <div>
      <Button :block="true">Button Block</Button>
    </div>

    <h2>Badges</h2>
    <div>
      <Button :badged="true">
        Button
        <Badge value="New"/>
      </Button>
      <Button :badged="true">
        Button
        <Badge modifier="danger" value="1"/>
      </Button>
      <Button :badged="true">
        Button
        <Badge modifier="warning" value="9"/>
      </Button>
      <Button :badged="true">
        Button
        <Badge modifier="success"/>
      </Button>
      <Button :badged="true">
        Button
        <Badge modifier="info"/>
      </Button>
    </div>

    <h2>Avatar</h2>
    <div>
      <Avatar
              border-radius="50%"
              :size="100"
              img="https://images.unsplash.com/photo-1511367461989-f85a21fda167?ixid=MXwxMjA3fDB8MHxzZWFyY2h8Mnx8cHJvZmlsZXxlbnwwfHwwfA%3D%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=500&q=60"
      />
      <Avatar
              border-radius="10px"
              img="https://images.unsplash.com/photo-1457449940276-e8deed18bfff?ixid=MXwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHw%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=1350&q=80"
      />
      <Avatar
              type="text"
              border-radius="50%"
              text="Jack"

      />
    </div>

    <h2>Card</h2>
    <div class="card-grid">
      <Card image="https://images.unsplash.com/photo-1609349589857-e5a172725169?ixid=MXwxMjA3fDB8MHxlZGl0b3JpYWwtZmVlZHwxMnx8fGVufDB8fHw%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=500&q=60" destination="https://www.reddit.com"/>
      <Card :lineLimit="4" destination="https://www.reddit.com" target="_blank"/>
    </div>
  </div>
</template>

<style lang="scss">

  .card-grid {
    display: grid;
    grid-template-columns: 1fr;
    grid-gap: 15px;
    max-width: 350px;
  }
</style>