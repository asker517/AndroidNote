import java.util.List;

import android.content.Context;
import android.util.SparseArray;
import android.view.View;
import android.view.ViewGroup;
import android.widget.BaseAdapter;

/**
 * BaseAdaper基类
 *
 * @author Anonymous
 * @data: 2014年9月2日 下午5:31:07
 * @version: V1.0
 */
public abstract class ORBaseAdapter<T> extends BaseAdapter {
  protected Context mContext;
  protected List<T> mData;

  public ORBaseAdapter(Context mContext, List<T> mData) {
    this.mContext = mContext;
    this.mData = mData;
  }

  @Override public int getCount() {
    return mData.size();
  }

  @Override public T getItem(int position) {
    if (position >= mData.size()) {
      return null;
    }
    return mData.get(position);
  }

  @Override public long getItemId(int position) {
    return position;
  }


  /**
   * 返回Item布局的res id
   *
   * @return int res id
   */
  public abstract int getItemLayoutRes();

  /**
   * 使用该getItemView方法替换原来的getView方法，需要子类实现
   */
  public abstract View getItemView(int position, View convertView, ViewHolder holder);

  @SuppressWarnings("unchecked") @Override public View getView(int position, View convertView,
      ViewGroup parent) {
    ViewHolder holder;
    if (null == convertView) {
      convertView = View.inflate(mContext, getItemLayoutRes(), null);
      holder = new ViewHolder(convertView);
      convertView.setTag(holder);
    } else {
      holder = (ViewHolder) convertView.getTag();
    }
    return getItemView(position, convertView, holder);
  }

  /**
   * BaseViewHolder
   *
   * @author Anonymous
   * @data: 2014年9月2日 下午5:18:43
   * @version: V1.0
   */
  public class ViewHolder {
    private SparseArray<View> views = new SparseArray<View>();
    private View convertView;

    public ViewHolder(View convertView) {
      this.convertView = convertView;
    }

    @SuppressWarnings("unchecked") public <T extends View> T getView(int resId) {
      View v = views.get(resId);
      if (null == v) {
        v = convertView.findViewById(resId);
        views.put(resId, v);
      }
      return (T) v;
    }
  }

  public void addAll(List<T> elem) {
    mData.addAll(elem);
    notifyDataSetChanged();
  }

  public void remove(T elem) {
    mData.remove(elem);
    notifyDataSetChanged();
  }

  public void remove(int index) {
    mData.remove(index);
    notifyDataSetChanged();
  }

  public void replaceAll(List<T> elem) {
    mData.clear();
    mData.addAll(elem);
    notifyDataSetChanged();
  }
}
