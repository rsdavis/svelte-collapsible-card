

<script>
    import CollapsibleCard from './CollapsibleCard.svelte'
</script>


<CollapsibleCard className='card' open={false}>
    <div slot='header'>header</div>
    <div slot='body'>
        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Praesentium perferendis maxime laborum corrupti molestias vitae nesciunt voluptatum tenetur? Quas numquam at voluptate! Laboriosam similique, officia error quisquam cupiditate quos delectus.</p>
        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Praesentium perferendis maxime laborum corrupti molestias vitae nesciunt voluptatum tenetur? Quas numquam at voluptate! Laboriosam similique, officia error quisquam cupiditate quos delectus.</p>
        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Praesentium perferendis maxime laborum corrupti molestias vitae nesciunt voluptatum tenetur? Quas numquam at voluptate! Laboriosam similique, officia error quisquam cupiditate quos delectus.</p>
        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Praesentium perferendis maxime laborum corrupti molestias vitae nesciunt voluptatum tenetur? Quas numquam at voluptate! Laboriosam similique, officia error quisquam cupiditate quos delectus.</p>
    </div>
</CollapsibleCard>

<CollapsibleCard className='card' open={true}>
    <div slot='header'>header</div>
    <div slot='body'>
        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Praesentium perferendis maxime laborum corrupti molestias vitae nesciunt voluptatum tenetur? Quas numquam at voluptate! Laboriosam similique, officia error quisquam cupiditate quos delectus.</p>
        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Praesentium perferendis maxime laborum corrupti molestias vitae nesciunt voluptatum tenetur? Quas numquam at voluptate! Laboriosam similique, officia error quisquam cupiditate quos delectus.</p>
        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Praesentium perferendis maxime laborum corrupti molestias vitae nesciunt voluptatum tenetur? Quas numquam at voluptate! Laboriosam similique, officia error quisquam cupiditate quos delectus.</p>
        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Praesentium perferendis maxime laborum corrupti molestias vitae nesciunt voluptatum tenetur? Quas numquam at voluptate! Laboriosam similique, officia error quisquam cupiditate quos delectus.</p>
    </div>
</CollapsibleCard>

<style>
    :global(.card) {
        width: 400px;
        border-bottom: 1px solid black;
    }
</style>