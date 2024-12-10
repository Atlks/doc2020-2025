需求修改说明 wdprs

增加栏位内容 L1413
    protected function single_row_columns( $item ) {


D:\user\ati\0src\wordpress\wp-admin\includes\class-wp-list-table.php

增加烂尾 L1266
    public function display() {

<table class="wp-list-table <?php echo implode( ' ', $this->get_table_classes() ); ?>">
    <thead>
    <tr>
        <?php $this->print_column_headers(); ?>
        <td>同步状态</td><td>分享状态</td>


ALTER TABLE `wp_posts`
ADD COLUMN `synstt`  int NULL DEFAULT 0 AFTER `comment_count`,
ADD COLUMN `shrstt`  int(255) NULL DEFAULT 0 AFTER `synstt`;



    protected function single_row_columns( $item ) {
   var_dump($item);
        die();


:\user\ati\0src\wordpress\wp-admin\includes\class-wp-list-table.php:1414:object(WP_Post)[7899]
  public 'ID' => int 8
  public 'post_author' => string '1' (length=1)
  public 'post_date' => string '2022-05-12 14:31:29' (length=19)
  public 'post_date_gmt' => string '2022-11-11 11:11:11' (length=19)
  public 'post_content' => string '<!-- wp:paragraph -->
<p>tttt2xxxxxxxs</p>

